<template>
	<div>
		<div id="btns-block">
			<button class="myButton" @click="ranBlock" v-bind:class="{randomTask}" ref="btn-random">
				Get a random activity
			</button>
			<button class="myButton" @click="searchBlock" v-bind:class="{searchTask}" ref="btn-search">
				Search for Activity
			</button>
		</div>

		<div id="random-block" v-if="randomTask">
			<div id="act-line">
				<p><span class="small-heads">Activity:</span> {{ activity }}</p>
			</div>
			<div>
				<p><span class="small-heads">Type:</span> {{ type }}</p>
			</div>
			<div>
				<p><span class="small-heads">participants:</span> {{ participants }}</p>
			</div>
			<div>
				<p><span class="small-heads">Price:</span> {{ price }}</p>
			</div>

			<button v-if='selectedAct===""' id="next-btn1" @click="getRandActivity">Get next activity</button><button v-else class="next-btn2" @click="getSelectedActivity(selectedAct)">Get next activity</button>
		</div>

		<div id="search-block" v-if="searchTask">
			<div>
				<label>Type of activity: </label>
				<select v-model="selectedAct">
					<option v-for="task in tasks" :key="task.id">{{task}}</option>
				</select>

			</div>
			<button class="next-btn2" @click="getSelectedActivity(selectedAct)">Get activity</button>
		</div>
	</div>
</template>

<script>
	import axios from "axios";

	export default {
		components: {},
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
	#random-block {
		width: 100%;
		border: 1px solid;
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
		height: 5rem;
		background: linear-gradient(45deg,#134E5E, #71B280);
		color: #ffffff;
		padding: 1rem;
		position: relative;
		top: 1rem;
	}

	#random-block {
		text-align: left;
		background: linear-gradient(45deg, #71B280,#134E5E);
		color: #ffffff;
		padding: 1rem;
		width: 90%;
		margin: auto;
		height: 20rem;
		font-size: 1.5rem;
		display: flex;
		flex-direction: column;
		justify-content: space-evenly;
		position: relative;
		top: 1rem;


	}

	#act-line {
		height: 6rem;

	}

	#random-block div {
		margin-bottom: -1rem;
	}

	#next-btn1 {
		position: relative;
		margin-top: 1.5rem;
		border:1px solid white;
		background-color:#310055;
		color: #ffffff;
		padding: 0.8rem;
		width:8rem;
		margin: auto;
	}

	.next-btn2 {
		width:8rem;
		border:1px solid white;
		background-color:#310055;
		color: #ffffff;
		padding: 0.5rem;
		margin: auto;
		margin-top:1rem;
	}
	select {
		width: 6rem;
		height: 1.5rem;
	}

	.small-heads {
		color:#310055;
	}

	.myButton {
		background: #3DF670;
		background-image: -webkit-linear-gradient(top, #3DF670, #0B5724);
		background-image: -moz-linear-gradient(top, #3DF670, #0B5724);
		background-image: -ms-linear-gradient(top, #3DF670, #0B5724);
		background-image: -o-linear-gradient(top, #3DF670, #0B5724);
		background-image: linear-gradient(to bottom, #3DF670, #0B5724);
		-webkit-border-radius: 20px;
		-moz-border-radius: 20px;
		border-radius: 20px;
		height: 0px;
		line-height: 0px;
		color: #FFFFFF;
		font-family: Open Sans;
		width: 15rem;
		font-size: 21px;
		font-weight: 100;
		padding: 20px;
		box-shadow: 0px 4px 0px 2px #000000;
		-webkit-box-shadow: 0px 4px 0px 2px #000000;
		-moz-box-shadow: 0px 4px 0px 2px #000000;
		text-shadow: 1px 1px 5px #000000;
		border: solid #0D772A 1px;
		text-decoration: none;
		display: inline-block;
		cursor: pointer;
		text-align: center;
	}

	.myButton:hover {
		border: solid #0D772A 1px;
		background: #0B5724;
		background-image: -webkit-linear-gradient(top, #0B5724, #3DF670);
		background-image: -moz-linear-gradient(top, #0B5724, #3DF670);
		background-image: -ms-linear-gradient(top, #0B5724, #3DF670);
		background-image: -o-linear-gradient(top, #0B5724, #3DF670);
		background-image: linear-gradient(to bottom, #0B5724, #3DF670);
		-webkit-border-radius: 20px;
		-moz-border-radius: 20px;
		border-radius: 20px;
		text-decoration: none;
	}

</style>
