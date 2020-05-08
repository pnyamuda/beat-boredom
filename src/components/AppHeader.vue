<template>
	<div id="intro-block">
		<div id="intro-background"> <img src="https://static.planetminecraft.com/files/resource_media/screenshot/1249/WALLPAPER-bored_4307916.jpg"></div>
		<p id="intro">Are you bored? There is a lot of activities you can do to beat the boredom.<br>

		</p>

		<div id="activity-intro">
			<p>Each activity gives you the following information:</p>
			<ul>
				<li>accessibility: A factor describing how possible an event is to do.<br>
					Zero being the most accessible -[0.0, 1.0]</li>
				<li>type: Type of the activity</li>
				<li>participants: The number of people that this activity could involve</li>
				<li>price:A factor describing the cost of the event with zero being free - [0, 1]</li>


			</ul>

		</div>
	</div>
</template>

<script>
	export default {
		name: "AppHeader",
		components: {

		},

	};

</script>

<style scoped>
	#intro-block {
	}
	
	#intro-background {
		width: 100%;
		
	}
	#intro-background img {
		width: 100%;
	}

	#intro {
		width: 100%;
		text-align: center;
		font-size: 1.5rem;

	}

	#activity-intro {
		border: 1ps solid;
		background: linear-gradient(45deg,#134E5E, #71B280);
		color: aliceblue;
		width: 95%;
		text-align: left;
		height: 16rem;
		padding: 1rem 0.5rem 1rem 0rem;
		margin: auto;
		line-height: 1.5rem;
	}

	#activity-intro p {
		text-align: center;
	}

</style>
