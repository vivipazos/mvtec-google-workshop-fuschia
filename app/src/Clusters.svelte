<script>
import {forceSimulation, forceX, forceY, forceCollide} from 'd3-force'

export let selectedObject;

// $: console.log('data', selectedObject);

const clusters = {
    "Australia fires": {
		x0: 200,
		y0: 400,
        color: '#333333'
	},
    "Yemen": {
		x0: 400,
		y0: 400,
        color: '#333333'
	},
	"Black Lives Matter": {
		x0: 500,
		y0: 400,
        color: '#333333'
	},
	"Coronavirus": {
		x0: 700,
		y0: 400,
        color: '#333333'
	},
    "Other": {
		x0: null,
		y0: null,
        color: '#cccccc'
	}
};

let width = 1000;
let height = 500;

let data = new Array(100).fill()
	.map(a => ({
		x: Math.random()*width,
		y: Math.random()*height,
        r: 10
	}));

const randomSimulation = forceSimulation(data)
    .on("tick", () => {
        data.forEach(d => {
            d.x = Math.max(10, Math.min(width-10, d.x));
            d.y = Math.max(10, Math.min(height-10, d.y));
        })
        data = data;
    })

const randomForce = function() {
    const str = 0.5;
    const r = data.map(d => {
        return {
            vx: str - Math.random() * str * 2,
            vy: str - Math.random() * str * 2
        };
    })
    return function(alpha) {
        for (var i = 0; i < data.length; ++i) {
            let d = data[i]
            if (d.x0 !== null) continue;
            d.vx = r[i].vx
            d.vy = r[i].vy;
        }
    }
}

window.setInterval(() => {
    randomSimulation
        .force('random', randomForce())
        .force("collide", forceCollide(d => d.r + 2))
        .alpha(1)
        .restart();
}, 500)

var prevComponent;
var clusterSimulation;
var annotations;

$: {
    if (prevComponent !== selectedObject) {
        let offset = 0;
        const clusterNames = Object.keys(selectedObject)
            .filter(key => key !== 'month')
            .sort();

        clusterNames.forEach(key => {
            for (var i = 0; i < selectedObject[key]; i++) {
                var d = data[offset+i];
                d.x0 = clusters[key].x0
                d.y0 = clusters[key].y0
                d.color = clusters[key].color;
                d.key = key;
            }
            offset += selectedObject[key]
        })


        const clusteredData = data.filter(d => d.key !== "Other")

        if (clusterSimulation) { clusterSimulation.stop(); }

        clusterSimulation = forceSimulation(clusteredData)
            .alphaDecay(0.0228 / 6)
            .velocityDecay(0.3)
            .force("x",forceX(d => d.x0 === null ? d.x : d.x0).strength(0.01))
            .force("y",forceY(d => d.y0 === null ? d.y : d.y0).strength(0.01))
            .force("collide", forceCollide(d => d.r + 2))
            .on("tick", () => data = data)

        annotations = clusterNames
            .filter(key => selectedObject[key] > 0 && key !== "Other")
            .map(key => {
                const c = clusters[key];
                return {
                    name: key,
                    x: c.x0,
                    y: c.y0,
                    r: Math.sqrt(selectedObject[key] * 10) * 5
                }
            });

        const antiCluster = clusterNames.map(key => {
            const c = clusters[key];
            return {
                fx: c.x0,
                fy: c.y0,
                r: Math.sqrt(selectedObject[key] * 10) * 5
            }
        })

        console.log(antiCluster);

        const randomNodes = data.filter(d => d.key === "Other")
        randomSimulation
            .nodes([...randomNodes, ...antiCluster])
    }
    prevComponent = selectedObject;
}


</script>

<main>
    <svg viewBox="0 0 {width} {height}">
        {#each data as d}
        <circle cx={d.x} cy={d.y} r={d.r} fill={d.color}/>
        {/each}
        {#each annotations as d}
        <circle cx={d.x} cy={d.y} r={d.r} fill="none" stroke="#333" data-name={d.name}/>
        <text x={d.x} y={d.y - d.r - 4}>
            {d.name}
        </text>
        {/each}
    </svg>
</main>

<style>

    svg {
        border: 1px solid black;
    }

    text {
        text-anchor: middle;
    }

</style>