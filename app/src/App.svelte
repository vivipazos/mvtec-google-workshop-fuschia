<svelte:head>
	<link rel="stylesheet" type="text/css" href="http://propublica.github.io/weepeople/weepeople.css">
</svelte:head>

<script>

	import Menu from './components/common/Menu.svelte'
	import Test from './test/Test.svelte'
	import Footer from './components/common/Footer.svelte'
	import Clusters from './Clusters.svelte'
	import Scroller from '@sveltejs/svelte-scroller';
	import dataScr from './data/Scrolly.json'
	import { Container, Row, Col, MaterialApp } from 'svelte-materialify';
	import InlineSVG from 'svelte-inline-svg';

	const chartDesktop = './assets/desktop-svg-chart.svg';
	const chartMobile = './assets/mobile-svg-chart.svg'

	let index = 0, offset, progress;

</script>

<main>
	<meta charset="UTF-8">
	<div class="header">
		<video autoplay muted id="myVideo">
			<source src="./assets/intro.mp4" type="video/mp4">
		</video>
	</div>
	<Scroller top={0} bottom={1} bind:index={index}>
		<div slot="background">
			<Clusters selectedObject={dataScr[index]}/>
		</div>

		<div slot="foreground">
			<section>
				<div class="text elevation-1 pa-8 text-left">
				<p>First, let's re-imagine the Google search index as 100 people, represented by these floating circles, <span class="weepeople">m</span> as <span class="dot"></span>.</p>
				</div>
			</section>

			<section>
				<div class="text elevation-1 pa-8 text-left">
				<p class="text-subtitle-1 text-center">DECEMBER 2019</p>
				<p>We start our story just before the pandemic hits.</p>
				<p><b>Three</b> of us banded together to help Australia during its worst bushfires in recent history - an <span class="cyan white-text font-weight-black rounded pa-1 mb-2 elevation-1">environmental</span> catastrophe.</p>
				</div>
			</section>
		
			<section>
				<div class="text elevation-1 pa-8 text-left">
				<p class="text-subtitle-1 text-center">JANUARY 2020</p>
				<p>Interest in helping the Australian bushfires peaked in January just as interest in <span class="purple white-text font-weight-black rounded pa-1 mb-2 elevation-1">Coronavirus</span> was growing.</p>
				</div>
			</section>

			<section>
				<div class="text elevation-1 pa-8 text-left">
				<p class="text-subtitle-1 text-center">FEBRUARY 2020</p>
				<p>In less than a month, everyone’s attention was elsewhere. Just <b>one person</b> was left caring about the <span class="cyan white-text font-weight-black rounded pa-1 mb-2 elevation-1">bushfires</span> while <span class="purple white-text font-weight-black rounded pa-1 mb-2 elevation-1">Coronavirus</span> interest rose to <b>five people</b>.</p>
				</div> 
			</section>

			<section>
				<div class="text elevation-1 pa-8 text-left">
				<p class="text-subtitle-1 text-center">MARCH 2020</p>
				<p>At the peak of the first wave, almost everyone was trying to search ways to help with <span class="purple white-text font-weight-black rounded pa-1 mb-2 elevation-1">Coronavirus</span>.</p>
				</div>
			</section>

			<section>
				<div class="text elevation-1 pa-8 text-left">
				<p class="text-subtitle-1 text-center">APRIL 2020</p>
				<p>Slowly, people drifted away. A month later, the number of people searching how to help with <span class="purple white-text font-weight-black rounded pa-1 mb-2 elevation-1">Coronavirus</span> dropped by a third.
				</div>
			</section>

			<section>
				<div class="text elevation-1 pa-8 text-left">
				<p class="text-subtitle-1 text-center">MAY 2020</p>
				<p>Just two months after its peak, interest in <span class="purple white-text font-weight-black rounded pa-1 mb-2 elevation-1">Coronavirus</span> dropped to just <b>16 people</b>.</p>
				<p>Attention shifted as a result of George Floyd's horrific death, uniting people to help the <span class="yellow font-weight-black rounded pa-1 mb-2 elevation-1">Black Lives Matter protest</span> movement.</p>
				</div>
			</section>

			<section>
				<div class="text elevation-1 pa-8 text-left">
				<p class="text-subtitle-1 text-center">JUNE 2020</p>
				<p><span class="yellow font-weight-black rounded pa-1 mb-2 elevation-1">Black Lives Matter</span> peaks in the month following George Floyd's death. Yemen’s humanitarian crisis worsens as a result of <span class="purple white-text font-weight-black rounded pa-1 mb-2 elevation-1">Coronavirus</span>, triggering a UN meeting and a flurry of support, too.
				</p>
				</div>
			</section>

			<section>
				<div class="text elevation-1 pa-8 text-left">
				<p class="text-subtitle-1 text-center">JULY 2020</p>
				<p>Less than a fifth of people are still searching how to help with the <span class="yellow font-weight-black rounded pa-1 mb-2 elevation-1">Black Lives Matter</span> protests, falling dramatically in just a month. And, looking back at all the data since 2015, these attention shifts is very common for <b>major crisis events</b>...</p>
				</div>
			</section>
		</div>
	  </Scroller>
	<MaterialApp>
	  <Container>
		<Row>
		<Col cols={1} sm={1} md={2} lg={3}></Col>
		<Col cols={10} sm={10} md={8} lg={6}>
			<h2 class="text-h2 a-8">Human solidarity, as it turns out, is <b>strong</b> but fleeting.</h2>
			<div class="text-body-1">
				<p>We band together quickly in times of need, gathering support at crucial times.</p>
				<p>But, our focus fades just as quickly - at least this is the trend for most of the events we analysed since 2015.</p>
			</div>
		</Col>
		<Col cols={1} sm={1} md={2} lg={3}></Col>
		</Row>

		<Row>
			<Col cols={1} sm={1} md={2} lg={2}></Col>
			<Col cols={10} sm={10} md={8} lg={8}>
				<div class="desktop">
					<InlineSVG src={chartDesktop}/>
				</div>
				<div class="mobile">
					<InlineSVG src={chartMobile}/>
				</div>
			</Col>
			<Col cols={1} sm={1} md={2} lg={2}></Col>
			</Row>

		<Row>
			<Col cols={1} sm={1} md={2} lg={3}></Col>
			<Col cols={10} sm={10} md={8} lg={6}>
			<div class="text-body-1">
				<p>No surprises that help for <b>coronavirus</b> far outstrips any other major humanitarian crisis since 2015.
				<p>But <b>Puerto Rico</b> actually ranks as the second-highest because of the disastrous <b>Hurricane Maria</b> that killed at least <b>3,087 people</b> in <b>Sept 2017</b>.</p>
				<p>It even got more search interest than <b>Black Lives Matter</b> and held people’s interest longer than average.</p>
			</div>
			</Col>
			<Col cols={1} sm={1} md={2} lg={3}></Col>
		</Row>

		<Row>
			<Col cols={0} sm={0} md={0} lg={1}></Col>
			<Col cols={12} sm={12} md={12} lg={10}>
			<img src="./assets/hurricaneMaria.jpg" alt="An image of the destruction after Hurricane Maria wiped out entire streets on Sept 19, 2017." width="100%" />
			<div class="text-caption">People stand amid the destruction on the morning after Hurricane Maria destroyed much of Puerto Rico. Photo: <a href="https://www.flickr.com/photos/rooseveltskerrit/37372721465/">Flickr by Roosevelt Skerrit</a></div>
			</Col>
			<Col cols={0} sm={0} md={0} lg={1}></Col>
		</Row>

		<Row>
			<Col cols={1} sm={1} md={2} lg={3}></Col>
			<Col cols={10} sm={10} md={8} lg={6}>
			<div class="text-body-1">
				<p>The devastation was immediate and lasting. Many people lost their lives.</p>

				<p>Realising the sheer immensity of repairing the damage, humanity banded together almost <b>three times</b> more than average.</p>
			</div>
			</Col>
			<Col cols={1} sm={1} md={2} lg={3}></Col>
		</Row>

		<Row>
			<Col cols={1} sm={1} md={2} lg={3}></Col>
			<Col cols={10} sm={10} md={8} lg={6}>
			<div class="text-body-1">
				<p>INSERT COMPARATIVE GRAPHIC HERE</p>
			</div>
			</Col>
			<Col cols={1} sm={1} md={2} lg={3}></Col>
		</Row>

		<Row>
			<Col cols={1} sm={1} md={2} lg={3}></Col>
			<Col cols={10} sm={10} md={8} lg={6}>
			<div class="text-body-1">
				<p>INSERT SMALL MULTIPLES HERE</p>
			</div>
			</Col>
			<Col cols={1} sm={1} md={2} lg={3}></Col>
		</Row>

		<Row>
			<Col cols={1} sm={1} md={2} lg={3}></Col>
			<Col cols={10} sm={10} md={8} lg={6}>
			<h2 class="text-h2 a-8"> Humans band together in times of crisis when we <b>need it most</b>.</h2>
			<div class="text-body-1">
				<p>Some final comments here.</p>
			</div>
			</Col>
			<Col cols={1} sm={1} md={2} lg={3}></Col>
		</Row>
		
		
		</Container>
	</MaterialApp>
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
		padding-top: 20vh;
		text-align: center;
		max-width: 450px;
		margin: 0 auto;
		font-size: 25px;
	}

	.text {
		background-color: hsla(0,0%,100%,.9);
	}

	.weepeople {
		font-size: 30px;
		color: #9F9F9F;
	}

	.desktop  {
		display: none;
		min-width: 480px;
	}

	.mobile {
		display: block;
		width: 100%;
		/* max-width: 480px; */
	}

	@media only screen and (min-width:600px){
		.mobile {
			display: none;
		}
		.desktop {
			display:block;
			max-width: 1200px;
			margin: 0 auto;
		}

	
</style>