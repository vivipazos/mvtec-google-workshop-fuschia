<script>
	import Menu from './components/common/Menu.svelte'
	import Test from './test/Test.svelte'
	import Footer from './components/common/Footer.svelte'
	// import Random from './components/common/Random.svelte'

</script>

<main>
	<h1>We all want to <strong>help</strong>.</h1>
	<h2>But, according to Google search, not for <strong>long enough</strong>.</h2>
	<p>Let's reimagine the Google search index as 100 people, represented by these floating circles.</p>
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

	h1, h2, p {
		max-width: 500px;
		margin: 0 auto;
		text-align: center;
		padding: 50px;
	}

</style>