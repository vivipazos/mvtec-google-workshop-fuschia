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
let height = 600;

let data = new Array(100).fill()
	.map(a => ({
		x: Math.random()*width,
		y: Math.random()*height,
	}));

const randomSimulation = forceSimulation(data)
    .on("tick", () => data = data)

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
    randomSimulation.force('random', randomForce())
    randomSimulation.alpha(1);
    randomSimulation.restart();
}, 500)

var prevComponent;
var clusterSimulation;
$: {
    if (prevComponent !== selectedObject) {
        let offset = 0
        Object.keys(selectedObject)
            .filter(key => key !== 'month')
            .sort()
            .forEach(key => {
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
            .force("x",forceX(d => d.x0 === null ? d.x : d.x0))
            .force("y",forceY(d => d.y0 === null ? d.y : d.y0))
            .force("collide", forceCollide(12))
            .on("tick", () => data = data)
    }
    prevComponent = selectedObject;
}


</script>

<main>
    <svg viewBox="0 0 {width} {height}">
        {#each data as d}
        <circle cx={d.x} cy={d.y} r="10" fill={d.color}/>
        {/each}
    </svg>
</main>

<style>

</style>