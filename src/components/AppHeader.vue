<template>
	<div>
		<h1>
			<h1>Beat Boredom</h1>
		</h1>
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
	h1 {
		background-color: navy;
		color: aliceblue;
		text-align: center;
		width: 100%;

	}

	#intro {
		width: 100%;
		text-align: center;

	}

	#activity-intro {
		border: 1ps solid;
		background-color:grey;
		color: aliceblue;
		width: 100%;
		text-align:left;
	}
	#activity-intro p {
		text-align: center;
	}

</style>
