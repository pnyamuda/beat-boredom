<template>
	<div id="intro-block">
		<div id="intro-background"> <img src="https://static.planetminecraft.com/files/resource_media/screenshot/1249/WALLPAPER-bored_4307916.jpg"></div>
		<p id="intro">Are you bored? If you suffer from the same lack of enthusiasm,  beat the boredom of days at home alone!  There is a lot of activities you can do to beat the boredom.  find the things that actually engage us.<br>

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
		height: 12rem;
		padding: 1rem 0.5rem 2rem 0rem;
		margin: auto;
		line-height: 1.5rem;
		border-radius: 10px;
	}

	#activity-intro p {
		text-align: center;
	}
	@media (min-width:480.1px) and (max-width:768px) {
		#activity-intro {
			padding-bottom:0rem;
		}
		
	}
	@media (min-width:768px) {
		#activity-intro {
			padding-bottom:0rem;
			width: 50rem;
		}
		#intro {
			width: 60rem;
			margin: auto;
		}
		
		
	}

</style>
