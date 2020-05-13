<template>
	<div id="whole-random-block">
		<div id="btns-block">
			<button class="myButton" @click="ranBlock" v-bind:class="{randomTask}" ref="btn-random">
				Get a random activity
			</button>
			<button class="myButton" @click="searchBlock" v-bind:class="{searchTask}" ref="btn-search">
				Search for Activity
			</button>
		</div>

		<transition name="fade">

			<div id="random-block" v-if="randomTask">


				<div id="other-information">

					<p><span class="small-heads">Type:</span> {{ type }}</p>

					<p><span class="small-heads">Price:</span> {{ price }}</p>


					<p><span class="small-heads">participants:</span> {{ participants }}</p>





				</div>

				<div id="act-line">
					<p><span class="small-heads">Activity:</span> {{ activity }}</p>

				</div>

				<button class="myButton" v-if='selectedAct===""' id="next-btn1" @click="getRandActivity">Get next activity</button><button v-else v-bind:class="{'next-btn2':true,myButton:true}" @click="getSelectedActivity(selectedAct)" id="second-random-btn">Get next activity</button>
			</div>

		</transition>



		<transition name="fade">
			<div id="search-block" v-if="searchTask">
				


				<div class="select" v-if="searchTask">
					<select name="slct" id="slct" v-model="selectedAct">
						<option selected disabled value="">Choose type of activity</option>
						<option v-for="task in tasks" :key="task.id">{{task}}</option>

					</select>
				</div>

				<button id="get-act-btn" v-bind:class="{'next-btn2':true,myButton:true}" @click="getSelectedActivity(selectedAct)">Get activity</button>
			</div>

		</transition>


	</div>
</template>

<script>
	import axios from "axios";

	export default {
		name: "RandomActivity",
		data() {
			return {
				randomTask: false,
				searchTask: false,
				activity: "activity",
				type: "type",
				participants: "participants",
				price: "price",
				tasks: [
					"education",
					"recreational",
					"social",
					"diy",
					"charity",
					"cooking",
					"relaxation",
					"music",
					"busywork"
				],
				selectedAct: "",
				show: true,
			};
		},

		methods: {
			getRandActivity() {
				axios
					.get("http://www.boredapi.com/api/activity/")
					.then(response => {
						console.log("rand function fired");
						this.activity = response.data.activity;
						this.type = response.data.type;
						this.participants = response.data.participants;
						this.price = response.data.price;

						this.selectedAct = "";
					});
			},
			ranBlock() {
				this.randomTask = true;
				this.searchTask = false;

				this.getRandActivity()

			},
			searchBlock() {
				this.searchTask = true;
				this.randomTask = false;

			},
			getSelectedActivity(type) {
				axios
					.get("http://www.boredapi.com/api/activity?type=" + type)
					.then(response => {
						console.log("get select fired")
						this.activity = response.data.activity;
						this.type = response.data.type;
						this.participants = response.data.participants;
						this.price = response.data.price;

						this.randomTask = true;
						this.searchTask = false;

					})
			}

		}
	};

</script>

<style scoped>
	select {
		-webkit-appearance: none;
		-moz-appearance: none;
		-ms-appearance: none;
		appearance: none;
		outline: 0;
		box-shadow: none;
		border: 0 !important;
		background: #2c3e50;
		background-image: none;
	}

	/* Remove IE arrow */
	select::-ms-expand {
		display: none;
	}

	/* Custom Select */
	.select {
		position: relative;
		display: flex;
		width: 15rem;
		height: 3em;
		line-height: 3;
		background: #2c3e50;
		overflow: hidden;
		border-radius: .25em;
	}

	select {
		flex: 1;
		padding: 0 .5em;
		color: #fff;
		cursor: pointer;
	}

	/* Arrow */
	.select::after {
		content: '\25BC';
		position: absolute;
		top: 0;
		right: 0;
		padding: 0 1em;
		background: #34495e;
		cursor: pointer;
		pointer-events: none;
		-webkit-transition: .25s all ease;
		-o-transition: .25s all ease;
		transition: .25s all ease;
	}

	/* Transition */
	.select:hover::after {
		color: plum;
	}






	.fade-enter-active,
	.fade-leave-active {
		transition: opacity .5s;
	}

	.fade-enter,
	.fade-leave-to

	/* .fade-leave-active below version 2.1.8 */
		{
		opacity: 0;
	}


	#btns-block {
		width: 100%;
		display: flex;
		flex-direction: row;
		justify-content: space-evenly;
		flex-wrap: wrap;
		height: 8rem;
		position: relative;
		top: 1.5rem;

	}

	.randomTask {
		background-color: red;
	}

	.searchTask {
		background: red;
	}

	#search-block {
		display: flex;
		flex-direction: column;
		justify-content: space-evenly;
		align-items: center;
		border: 1px solid;
		height: 10rem;
		border: 1px solid #ffffff;
		background: rgba(32, 32, 32, 0.6);
		color: #ffffff;
		padding: 1rem;
		position: relative;
		top: 2rem;
	}

	#random-block {
		position: relative;
		text-align: start;
		color: #ffffff;
		padding: 1rem;
		width: 90%;
		margin: auto;
		height: 14rem;
		display: grid;
		grid-template-rows: 30% 40% 30%;
		background: rgba(32, 32, 32, 0.6);
		border: 1px solid #ffffff;
		top: 3rem;
		border-radius: 10px;


	}

	#act-line {}

	#other-information {
		display: grid;
		grid-template-columns: 60% 40%;
		grid-template-rows: 50% 50%;
		grid-row-gap: 1%;
		margin-top: 0rem;
	}

	#random-block div {}

	#next-btn1 {
		margin: auto;
		width: 7rem;
		padding: 0.1rem;
		border-radius: 0px;
		margin-top: 0rem;
	}

	.next-btn2 {
		margin: auto;
		margin-top: 1rem;
	}

	#get-act-btn {
		width: 6rem;
		padding: 0.5rem;
		border-radius: 0px;
		margin-top: 1rem;

	}

	#second-random-btn {
		margin-top: -1rem;
		margin: auto;
		width: 7rem;
		padding: 0.1rem;
		border-radius: 0px;

	}

	select {}

	.small-heads {
		font-weight: bold;
		color: plum;
	}

	.myButton {
		-webkit-border-radius: 20px;
		-moz-border-radius: 20px;
		border-radius: 20px;
		color: #FFFFFF;
		font-family: Open Sans;
		font-weight: 100;
		height: 3rem;
		padding: 1rem;
		background-color: #310055;
		box-shadow: 1px 1px 20px 0px #000000;
		-webkit-box-shadow: 1px 1px 20px 0px #000000;
		-moz-box-shadow: 1px 1px 20px 0px #000000;
		text-shadow: 1px 1px 20px #000000;
		border: solid #FFFFFF 1px;
		text-decoration: none;
		display: inline-block;
		cursor: pointer;
		text-align: center;
		width: 12rem;
		transition: all 0.5s ease-in-out;
	}

	.myButton:hover {
		background: #6A4281;
		border: solid #FFFFFF 1px;
		-webkit-border-radius: 20px;
		-moz-border-radius: 20px;
		border-radius: 20px;
		text-decoration: none;
	}

	@media (min-width:480.1px) and (max-width:768px) {
		#random-block {
			top: 0rem;
		}

		#btns-block {
			top: 2rem;
		}

		#search-block {
			top: 0rem;
		}
		#whole-random-block {
			margin-top: 5rem;
		}
	}

	@media (min-width:768px) {
		#random-block {
			width: 50rem;
			top: 0rem;
			border-radius: 0px;
		}

		#btns-block {
			width: 40rem;
			margin: auto;
		}

		#search-block {
			top: 0rem;
			width: 40rem;
			margin: auto;
		}
		#whole-random-block {
			margin-top: 5rem;
		}
		
	}

</style>
