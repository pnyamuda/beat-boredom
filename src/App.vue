<template>
  <div id="app">
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

<style>

</style>
