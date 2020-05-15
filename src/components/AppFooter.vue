<template>
	<div>

		<footer>
			<p id="app-name">BeatBoredom</p>
			<p>&#169;2020</p>

		</footer>

	</div>
</template>

<script>
	export default {
		name: "AppFooter",
		components: {

		},

	};

</script>

<style scoped>
	#app-name {
		font-family: 'Lobster', cursive;
		font-size: 1.5rem;
		margin-bottom: -0.5rem;
	}
	footer {

		padding-top: 1rem;
		background-color: #310055;
		color: #ffffff;
		text-align: center;
		width: 100%;
		height: 5rem;
		display: flex;
		flex-direction: column;
		justify-content: center;
		position: absolute;
		top: 77rem;
		
	}
	@media (max-width:319px) {
		footer {
			top: 82rem;
		}
		
	}

	@media (min-width:480.1px) and (max-width:768px) {
		footer {
			top: 70rem;
		}
	}
	@media (min-width:768px) {
		footer {
			top:65rem;
		}
	}

</style>
