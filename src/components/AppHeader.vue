<template>
	<div id="intro-block">
		<p id="intro">From education, board games, cooking and self care to indoor gardening and organizing, here you can find a vast amount of exciting activities depending on your mood that will keep you entertained no matter how long you're stuck inside. If you're bored, then you can beat the BOREDOM and find the things that will actually engage you. Enjoy!

		</p>

		<div id="activity-intro">
			<p>Each activity gives you the following information:</p>
			<ul>
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
		width: 100%;
		position: relative;
	}


	#intro {
		width: 100%;
		text-align: center;
		font-size: 1.5rem;
		color: #ffffff;
		

	}

	#activity-intro {
		border: 1px solid white;
		position: relative;
		background: rgba(32, 32, 32, 0.6);
		width: 95%;
		text-align: left;
		height: 12rem;
		padding: 1rem 0.5rem 2rem 0rem;
		margin: auto;
		line-height: 1.5rem;
		border-radius: 10px;
		color: #ffffff;
	}

	#activity-intro p {
		text-align: center;
	}

	@media (min-width:480.1px) and (max-width:768px) {
		#activity-intro {
			padding-bottom: 0rem;
		}

		#intro {
			width: 80%;
			margin: auto;
		}

		#intro-block {
			top: 2rem;

		}

		#activity-intro {
			top: 2rem;

		}

	}

	@media (min-width:768px) {
		#activity-intro {
			padding-bottom: 0rem;
			width: 30rem;
		}

		#intro {
			width: 75%;
			margin: auto;
		}

		#activity-intro {
			top: 2rem;

		}

		#intro-block {
			top: 2rem;

		}


	}

</style>
