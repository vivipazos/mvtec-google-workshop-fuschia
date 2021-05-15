<script>
	import Menu from './components/common/Menu.svelte'
	import Test from './test/Test.svelte'
	import Footer from './components/common/Footer.svelte'
	import Clusters from './Clusters.svelte'
	import Scroller from '@sveltejs/svelte-scroller';
	import dataScr from './data/Scrolly.json'

	let index = 0, offset, progress;

</script>

<main>
<!-- 	<meta charset="UTF-8">
	<div class="header">
		<video autoplay muted loop id="myVideo">
			<source src="./assets/randomCircles_6.mp4" type="video/mp4">
		</video>
		<div class = "header-text">
			<h1>We all want to &#10024;&nbsp<strong>help</strong>&nbsp&#10024;.</h1>
			<h3>But, according to Google search, not for <strong>long enough</strong>.</h3>
			<h3>Let's reimagine the Google search index as 100 people, represented by these floating circles <span class="dot"></span>.</h3>
		</div>
	</div> -->
	<Scroller top={0} bottom={1} bind:index={index}>
		<div slot="background">
			<Clusters selectedObject={dataScr[index]}/>
		</div>

		<div slot="foreground">
			<section>We all want to ✨help✨. <br>
				But, according to Google search, not for <br> long enough. <br> <br> <br>
				Let’s reimagine the Google search index as 100 people,<br> represented by these floating circles.
			</section>

			<section>
				<h>DECEMBER  2019</h>
				We start our story in December 2019. Just before the pandemic hits. 
				Three of us cared about fires burning in Australia.
			</section>
		
			<section>
				<h>JANUARY 2020</h>
				Interest in helping for the Australian bushfires peaked in January, while interest in Coronavirus was just beginning. 
			</section>

			<section>
				<h>FEBRUARY 2020</h>
				In less than a month, everyone’s attention was elsewhere. Just one person was left caring about the bushfires while Coronavirus interest rose to five people. 
			</section>

			<section>
				<h>MARCH 2020</h>
				At the peak of the first wave, almost everyone was trying to search ways to help with Coronavirus. 
			</section>

			<section>
				<h>APRIL 2020</h>
				Slowly, people drifted away. A month later, the number of people searching how to help with Coronavirus dropped by a third.
			</section>

			<section>
				<h>MAY 2020</h>
				Just two months after its peak, interest in Coronavirus dropped to just 16 people. Black Lives Matter protests were on the rise.
			</section>

			<section>
				<h>JUNE 2020</h>
				The death of George Floyd sparks wide interest in the Black Lives Matter protest. Yemen’s crisis from Coronavirus also gets some interest.
			</section>

			<section>
				<h>JULY 2020</h>
				Less than a fifth of people are still searching how to help, falling dramatically in just a month. And, looking back at all the data since 2015, this is a common trend for crisis events.
			</section>
		</div>
	  </Scroller>
	<!-- <Test /> -->

	<!-- <Random /> -->

	<Footer>
		<div slot="about">
			Google search trends reveal a lot about what it...
		</div>
		<div slot="data">
			The data is indexed to...
		</div>
		<div slot="team">
			Rebecca Pazos, Rocío Márquez, Victor and Oriol.
		</div>
	</Footer>
</main>

<style>
	main {
		padding: 1em;
		padding-bottom: 0;
		margin: 0 auto;
	}

	h1, h3 {
		max-width: 600px;
		margin: 0 auto;
		text-align: center;
		padding: 50px;
	}

	.header-text {
		position: absolute;
		top: 10vh;
		margin-left: 30vw;
		background-color: hsla(0,0%,100%,.8);
		max-width: 600px;
		padding: 10px;
	}

	#myVideo {
  		right: 0;
  		bottom: 0;
  		min-width: 100%;
		min-height: 100%;
	}

	.dot {
  		height: 20px;
  		width: 20px;
  		background-color: #9F9F9F;
  		border-radius: 50%;
  		display: inline-block;
	}
	section {
		height: 80vh;
		text-align: center;
	}
</style>