<template>
  <div id="app">
	  <header>Beat Boring</header>
	<app-header></app-header>
	  <random-task></random-task>

    
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
	header {
		background-color:#310055;;
		color:#ffffff;
		text-align: center;
		width: 100%;
		height: 5rem;
		display: flex;
		flex-direction: column;
		justify-content: center;

	}
	

</style>
