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
			<p>Activity: {{ activity }}</p>
			<p>Type: {{ type }}</p>
			<p>participants:{{ participants }}</p>
			<p v-show="price !== ''">Price: {{ price }}</p>

			<button @click="getRandActivity">Get next activity</button>
		</div>

		<div id="search-block" v-if="searchTask">
			<div>
				<label>Type of activity:</label>
				<select v-model="selectedAct">
					<option v-for="task in tasks" :key="task.id">{{task}}</option>
				</select>

			</div>
			<button @click="getSelectedActivity(selectedAct)">Get next activity</button>
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
		width:15rem;
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
