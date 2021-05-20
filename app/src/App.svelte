<svelte:head>
	<link rel="stylesheet" type="text/css" href="http://propublica.github.io/weepeople/weepeople.css">
</svelte:head>

<script>

	import Menu from './components/common/Menu.svelte'
	import Footer from './components/common/Footer.svelte'
	import Clusters from './Clusters.svelte'
	import Scroller from '@sveltejs/svelte-scroller';
	import dataScr from './data/Scrolly.json'
	import { Container, Row, Col, MaterialApp, ItemGroup } from 'svelte-materialify';
	import InlineSVG from 'svelte-inline-svg';

	const chartDesktop = './assets/desktop-svg-chart.svg';
	const chartMobile = './assets/mobile-svg-chart.svg';
	const puertoRicoMonth1 = './assets/puertoRico-month1.svg';
	const puertoRicoMonth2 = './assets/puertoRico-month2.svg';
	const environment = './assets/environment.svg';
	const conflicts = './assets/conflicts.svg';
	const protests = './assets/protests.svg';
	const coronavirus = './assets/coronavirus.svg';

	let index = 0, offset, progress;

</script>

<main>
<MaterialApp>
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
				<p>Pandemics, wildfires, protests. What drove us to band together to help?
				<p>We found  some anwers in Google's search index but first, let's reimagine the  data as 100 people, represented by these floating circles <img src="./assets/grey-legend.png" class="legend"/>.</p>
				
				</div>
			</section>

			<section>
				<div class="text elevation-1 pa-8 text-left">
				<p>As they group together to offer help to those in need, the circles will change from grey to black <img src="./assets/black-legend.png" class="legend"/>.</p>
				</div>
			</section>

			<section>
				<div class="text elevation-1 pa-8 text-left">
				<p class="text-subtitle-1 text-center">DECEMBER 2019</p>
				<p>We start our story just before the pandemic hits.</p>
				<p><strong>Three</strong> of us banded together to help Australia during its worst bushfires in recent history - an <span class="cyan white-text font-weight-black rounded pa-1 mb-2 elevation-1">environmental</span> catastrophe.</p>
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
				<p>In less than a month, everyone’s attention was elsewhere. Just <strong>one person</strong> was left caring about the <span class="cyan white-text font-weight-black rounded pa-1 mb-2 elevation-1">bushfires</span> while <span class="purple white-text font-weight-black rounded pa-1 mb-2 elevation-1">Coronavirus</span> interest rose to <strong>five people</strong>.</p>
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
				<p>Just two months after its peak, interest in <span class="purple white-text font-weight-black rounded pa-1 mb-2 elevation-1">Coronavirus</span> dropped to just <strong>16 people</strong>.</p>
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
				<p>Less than a fifth of people are still searching how to help with the <span class="yellow font-weight-black rounded pa-1 mb-2 elevation-1">Black Lives Matter</span> protests, falling dramatically in just a month.</p>
					
				<p>And, looking back at all the data since 2015, these attention shifts are all too common for <strong>major crisis events</strong>...</p>
				</div>
			</section>
		</div>
	  </Scroller>

	  <Container>
		<Row>
		<Col cols={1} sm={0} md={2} lg={3}></Col>
		<Col cols={10} sm={12} md={8} lg={6}>
			<h1>Human solidarity, it turns out, is <strong>strong</strong> but fleeting.</h1>
			<div class="text-body-1">
				<p>We band together quickly in times of need, gathering immense support at crucial times.</p>
				<p>Unfortunately, our focus fades just as quickly - at least this is the trend for most of the events we analysed since 2015.</p>
			</div>
		</Col>
		<Col cols={1} sm={0} md={2} lg={3}></Col>
		</Row>

		<Row>
			<Col cols={0} sm={0} md={1} lg={1}></Col>
			<Col cols={12} sm={12} md={10} lg={10}>
				<div>
					<InlineSVG src={chartDesktop}/>
				</div>
				<!-- <div class="d-block d-sm-none">
					<InlineSVG src={chartMobile}/>
				</div> -->
			</Col>
			<Col cols={0} sm={0} md={1} lg={1}></Col>
			</Row>

		<Row>
			<Col cols={1} sm={1} md={2} lg={3}></Col>
			<Col cols={10} sm={10} md={8} lg={6}>
			<div class="text-body-1">
				<p>It may come as little surprise that help for the <strong>pandemic</strong> far outstrips any other major humanitarian crisis since 2015.
				<p>But <strong>Puerto Rico</strong> actually ranks as the second-highest because of the disastrous <strong>Hurricane Maria</strong> that killed at least <strong>3,087 people</strong> in <strong>Sept 2017</strong>.</p>
				<p>It even got more search interest than <strong>Black Lives Matter</strong> and held people’s interest longer than average.</p>
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

				<p>Realising the sheer immensity of repairing the damage, humanity banded together at a rate <b>two times</b> higher than average.</p>
			</div>
			</Col>
			<Col cols={1} sm={1} md={2} lg={3}></Col>
		</Row>

		<Row>
			<Col cols={0} sm={0} md={2} lg={3}></Col>
			<Col cols={12} sm={12} md={8} lg={6}>
			<div class="text-body-1">
				<p><span class="cyan font-weight-black rounded pa-1 mb-2 elevation-1">44 people</span> helped Puerto Rico in Sept 2017, the month the catastrophe took place...</p>
				<div>
					<InlineSVG src={puertoRicoMonth1}/>
				</div>
				<p>... compared with <span class="cyan font-weight-black rounded pa-1 mb-2 elevation-1">16 people</span> a month later.</p>
				<div>
					<InlineSVG src={puertoRicoMonth2}/>
				</div>
			</div>
			</Col>
			<Col cols={0} sm={0} md={2} lg={3}></Col>
		</Row>

		<Row>
			<Col cols={0} sm={0} md={2} lg={3}></Col>
			<Col cols={12} sm={12} md={8} lg={6}>
			
				<h3> Most help was offered to those in <span class="cyan font-weight-black rounded pa-1 mb-2 elevation-1">environmental</span> catastrophes.</h3>
				
				<div class="text-body-1">
					<div>
						<InlineSVG src={environment}/>
					</div>
					<p>Most of the help was focused on helping those in environmental catastrophes, like hurricanes, wildfires or floods. 

					<p>For example, <strong>Hurricane Harvey</strong> devastated most of Texas and Louisiana in August 2017, killing at least 107 and causing USD$125 billion.</p>
						
					<p>Most spikes also happen for those events which happened closer to the US, possible evidence of the bias of Google searchers. This includes Hurricane Maria in Sept 2017 which affected mostly <strong>Puerto Rico</strong>.</p>
						
					<p class="last-par">The only Asian catastrophe was <strong>Nepal’s earthquake</strong> in April 2015 that killed almost 9,000 people. It has the third highest death tally of all events analysed. </p>
				</div>

				<h3><span class="purple white-text font-weight-black rounded pa-1 mb-2 elevation-1">Coronavirus</span>, and other pandemic-related events, inspired humany solidarity like nothing else before it.</h3>
				
				<div class="text-body-1">
					<div>
						<InlineSVG src={coronavirus}/>
					</div>

					<p>It is probably no surprise that coronavirus saw the largest spike for help out of all the events analysed.</p>

					<p>Interestingly, you might be surprised to see <strong>Yemen</strong> in this category. This is because it’s spike in June 2020 is actually related to a UN meeting to discuss the awful impacts that coronavirus had on an already starving and impoverished nation.</p>

					<p class="last-par"><strong>India’s</strong> most recent spike is because of the overwhelming second wave of cases currently wreaking havoc across the South Asian country.</p>
				</div>

				<h3>Black Lives Matter inspired more help than other <span class="yellow font-weight-black rounded pa-1 mb-2 elevation-1">protest</span> movements.</h3>

				<div class="text-body-1">
					<div>
						<InlineSVG src={protests}/>
					</div>
					<p>Three events related to protests saw spikes in help. All of them were mostly driven by iconic moments.</p>

					<p>In the case of <strong>Black Lives Matter</strong>, the spike occurs just folllowing George Floyd’s brutal death at the hands of US police officers. Just a month later and support for the cause lost impetus even though another 25 died in the following protests.</p>
						
					<p>The indigenous protests at <strong>Standing Rock</strong> to protest against the Dakota access pipeline project saw the lowest number of searches but there was a sustained trend of help before and after its peak, most likely encouraged by the arrests of famous actors like Shailenne Woodley.</p>
						
					<p class="last-par">One non-US event stands out - the Khartoum massacre in <strong>Sudan</strong>. Following months of protests, the deadly event took place in June 2019 and saw 128 killed on the spot by armed forces. This saw more support at its peak than the indigenous protests at Standing Rock.</p>

				</div>

				<h3><span class="red white-text font-weight-black rounded pa-1 mb-2 elevation-1">Conflict-related</span> events like terroist attacks, mass shootings all inspired our solidarity, near and far.</h3>

				<div class="text-body-1">
					<div>
						<InlineSVG src={conflicts}/>
					</div>

					<p>Two mass shooting events, one terrorist attack and one civil war - which is still ongoing - have been grouped under conflicts.</p>

					<p><strong>Aleppo</strong> saw the greatest response right in the midst of the deadly Syrian war that saw more than 16,000 civilians killed in 2016 alone.</p>

					<p><strong>Orlando’s</strong> mass shooting was at a gay club in June 2016 that killed 49 people. <strong>Las Vegas’</strong> mass shooting occured in Oct 2017 killing 61.</p>

					<p class="last-par">The <strong>Paris</strong> spike is during the terroist attacks that happend in Nov 2015, that saw 130 killed.</p>
				</div>

			</Col>
			<Col cols={0} sm={0} md={2} lg={3}></Col>
		</Row>

		<Row>
			<Col cols={1} sm={1} md={2} lg={3}></Col>
			<Col cols={10} sm={10} md={8} lg={6}>
			<h1> Humans band together in times of crisis when we <strong>need it most</strong>.</h1>
			<div class="text-body-1">
				<p>Some final comments here.</p>
			</div>
			</Col>
			<Col cols={1} sm={1} md={2} lg={3}></Col>
		</Row>
	</Container>

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
</MaterialApp>
</main>

<style>

	main {
		padding: 1em;
		padding-bottom: 0;
		margin: 0 auto;
	}

	h1 {
		line-height: 4rem;
	}

	h3 {
		line-height: 3rem;
	}

	strong {
		font-weight: 600;
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
		height: 100vh;
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

	.last-par {
		padding-bottom: 40px;
	}

	.legend {
		width: 60px;
	}
	
</style>