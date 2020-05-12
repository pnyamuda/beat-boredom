<template>
  <div id="app">
	  <header>BeatBoredom</header>
	<app-header></app-header>
	  <random-task></random-task>
<footer>
	<p>BeatBoredom</p>
	<p>&#169;2020</p>
	
	</footer>
    
  </div>
</template>

<script>

import AppHeader from "./components/AppHeader.vue";
import RandomActivity from "./components/RandomActivity.vue";
	
export default {
  name: "App",
  components: {
	  "app-header":AppHeader,
	  "random-task":RandomActivity,
   
  }
};
</script>

<style scoped>
	header,footer {
		background-color:#310055;;
		color:#ffffff;
		text-align: center;
		width: 100%;
		height: 5rem;
		display: flex;
		flex-direction: column;
		justify-content: center;

	}
	footer {
		position: relative;
		top: 5rem;
	}
	

</style>
