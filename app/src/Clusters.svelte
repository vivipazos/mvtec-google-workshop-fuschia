<script>
import dataScr from './data/Scrolly.json'
import {forceSimulation, forceX, forceY, forceCollide} from 'd3-force'
import { tick } from 'svelte';

export let selectedObject;

let dataTest = {
    "Australia fires": 24,
    "Coronavirus": 2,
    "Yemen": 0,
    "Black Lives Matter": 0,
    "Other": 74
  }
const clusters = {
    "Australia fires": {
		x0: 800,
		y0: 100,
	},
    "Yemen": {
		x0: 700,
		y0: 300,
	},
	"Black Lives Matter": {
		x0: 200,
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
let keys = Object.keys(selectedObject).filter(key => key !== 'month')

let width = 1000;
let height = 500;
let data = new Array(100).fill()
	.map(a => ({
		x: Math.random()*width,
		y: Math.random()*height,
	}));

$: {let offset = 0
    keys.forEach(key=> {
        for (var i = 0; i < selectedObject[key]; i++) {
            data[offset+i].x0 = clusters[key].x0
            data[offset+i].y0 = clusters[key].y0
            }
        offset += selectedObject[key]
    })
}

const simulation = forceSimulation(data)
.on("tick", () => data = data)
.force("collide",forceCollide(12))

function updateSimulation() { 
    simulation
    .force("x",forceX(d => d.x0 === null ? d.x : d.x0))
    .force("y",forceY(d => d.y0 === null ? d.y : d.y0))
}

$: selectedObject && updateSimulation();    

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