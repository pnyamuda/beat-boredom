<template>
	<div id="app">
		<vue-particles color="#dedede" :particleOpacity="0.7" :particlesNumber="80" shapeType="circle" :particleSize="4" linesColor="#dedede" :linesWidth="1" :lineLinked="true" :lineOpacity="0.4" :linesDistance="150" :moveSpeed="3" :hoverEffect="true" hoverMode="grab" :clickEffect="true" clickMode="push">
		</vue-particles>

		<div id="my-content">

			<header>BeatBoredom</header>
			<app-header></app-header>
			<random-task></random-task>
			<app-footer></app-footer>

		</div>
	</div>
</template>

<script>
	import AppHeader from "./components/AppHeader.vue";
	import RandomActivity from "./components/RandomActivity.vue";
	import AppFooter from "./components/AppFooter.vue";


	export default {
		name: "App",
		components: {
			"app-header": AppHeader,
			"random-task": RandomActivity,
			"app-footer": AppFooter,

		}
	};

</script>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Lobster&family=Roboto&display=swap');

	body {
		font-family: 'Roboto', sans-serif;
		background-color: #121212;
		width: 99%;
	}

	#my-content {
		position: absolute;
		top: 0rem;
		width: 99%;
	}

	header {
		background-color: #310055;
		color: #ffffff;
		text-align: center;
		width: 100%;
		height: 5rem;
		display: flex;
		flex-direction: column;
		justify-content: center;
		font-family: 'Lobster', cursive;
		font-size: 2rem;

	}

</style>
