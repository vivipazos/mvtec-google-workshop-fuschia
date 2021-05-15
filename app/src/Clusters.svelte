<script>
import dataScr from './data/Scrolly.json'
import {forceSimulation, forceX, forceY} from 'd3-force'

let dataTest = {
    "Australia fires": 24,
    "Coronavirus": 2,
    "Yemen": 0,
    "Black Lives Matter": 0,
    "Other": 74
  }
const clusters = {
    "Australia fires": {
		x0: 200,
		y0: 400,
	},
    "Yemen": {
		x0: 150,
		y0: 300,
	},
	"Black Lives Matter": {
		x0: 100,
		y0: 400,
	},
	"Coronavirus": {
		x0: 400,
		y0: 400
	},
    "Other": {
		x0: null,
		y0: null
	}
};
let keys = Object.keys(dataTest)

let width = 1000;
let height = 800;
let data = new Array(100).fill()
	.map(a => ({
		x: Math.random()*width,
		y: Math.random()*height
	}));

let offset = 0
keys.forEach(key=> {
    for (var i = 0; i < dataTest[key]; i++) {
        data[offset+i].x0 = clusters[key].x0
        data[offset+i].y0 = clusters[key].y0
        }
    offset += dataTest[key]
})
    
const simulation = forceSimulation(data)
                    .force("x",forceX(d => d.x0))
                    .force("y",forceY(d => d.y0))
                ;

</script>

<main>
    <svg viewBox="0 0 {width} {height}">
        {#each data as d}
        <circle cx={d.x} cy={d.y} r="10"/>
        {/each}
    </svg>
</main>

<style>

</style>