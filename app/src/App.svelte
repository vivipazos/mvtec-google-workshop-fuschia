<script>
	import Menu from './components/common/Menu.svelte'
	import Test from './test/Test.svelte'
	import Footer from './components/common/Footer.svelte'
	// import Random from './components/common/Random.svelte'

</script>

<main>
	<meta charset="UTF-8">
	<div class="header">
		<video autoplay muted loop id="myVideo">
			<source src="./assets/randomCircles_6.mp4" type="video/mp4">
		</video>
		<div class = "header-text">
			<h1>We all want to &#10024;&nbsp<strong>help</strong>&nbsp&#10024;.</h1>
			<h3>But, according to Google search, not for <strong>long enough</strong>.</h3>
			<h3>Let's reimagine the Google search index as 100 people, represented by these floating circles <span class="dot"></span>.</h3>
		</div>
	</div>
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
</style>