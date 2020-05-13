<template>
	<div id="app">
		<vue-particles color="#dedede" :particleOpacity="0.7" :particlesNumber="80" shapeType="circle" :particleSize="4" linesColor="#dedede" :linesWidth="1" :lineLinked="true" :lineOpacity="0.4" :linesDistance="150" :moveSpeed="3" :hoverEffect="true" hoverMode="grab" :clickEffect="true" clickMode="push">
		</vue-particles>

		<div id="con">

			<header>BeatBoredom</header>
			<app-header></app-header>
			<random-task></random-task>
			<footer>
				<p>BeatBoredom</p>
				<p>&#169;2020</p>

			</footer>

		</div>
		
		
		
	</div>
</template>

<script>
	import AppHeader from "./components/AppHeader.vue";
	import RandomActivity from "./components/RandomActivity.vue";

	export default {
		name: "App",
		components: {
			"app-header": AppHeader,
			"random-task": RandomActivity,

		}
	};

</script>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Merriweather&family=Roboto&display=swap');

	body {
		font-family: 'Roboto', sans-serif;
		background-color: #121212;
		width: 99%;
	}
	
	#con {
		position: absolute;
		top: 0rem;
		width: 99%;
	}

	header,
	footer {
		background-color: #310055;
		;
		color: #ffffff;
		text-align: center;
		width: 100%;
		height: 5rem;
		display: flex;
		flex-direction: column;
		justify-content: center;

	}

	footer {
		position: relative;
		top:35vh;
		padding-top: 1rem;
	}

</style>
