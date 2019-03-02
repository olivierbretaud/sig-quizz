<template>
	<div id="app" class="bg-img">
	<Start/>
	<div v-for="data in quizz" v-bind:key="data.id">
		<Question v-bind:id="data.id" v-bind:questionData="data" @count="counter()" @progress="progress()"/>
		<div class="progress-container">
			<div class="progress">
				<div class="progress-bar" role="progressbar" v-bind:style="{width: progressSum + '%'} "  aria-valuemin="0" aria-valuemax="100"></div>
			</div>
		</div>
	</div>
	<End id="end" v-bind:totalCount="userResponse"/>
	</div>
</template>

<script>
import Start from './components/Start.vue'
import Question from './components/Question.vue'
import End from './components/End.vue'
import data from './assets/quizz_data.json'

export default {
	name: 'app',

	components: {
		Start,
		Question,
		End
	},

	data() {
		return {
			quizz: data.quizz,
			userResponse: 0,
			progressSum: 0
		};
	},

	methods: {
		progress() {
			this.progressSum = this.progressSum +10
			return this.progressSum
		},
		counter() {
			this.userResponse = this.userResponse + 10
			return this.userResponse
		}
	}

}

</script>

<style>
#app {
	font-family: 'Open Sans', sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #3d4146;
	overflow-x: hidden;
}

.bg-img {
	background-image: url("./assets/bg-picture-grey.png");
	background-position: center; /* Center the image */
	background-attachment: fixed;
	background-repeat: no-repeat; /* Do not repeat the image */
	background-size: cover;
}

.lora {
	font-family: 'Lora', serif;
}

.lora-bold {
	font-family: 'Lora', serif;
	font-weight: 700
}

.container-fluid {
	min-height: 100vh;
}

.red {
	color: rgb(145, 10, 10);
}

.green {
	color: rgb(45, 121, 15);
}

.progress-container {
	position: fixed;
	bottom: -4px;
	height: 20px;
	width: 102%;
	left: -2px;
}

.custom-button {
	background-color: rgb(189, 15, 15);
	border-radius: 25px;
	color: white;
}

.custom-button:active {
	background-color: rgb(145, 10, 10);
}

.custom-button:hover {
	background-color: rgb(145, 10, 10);
}

.btn:focus {
	outline: 0;
	box-shadow: 0 0 0 0.2rem rgba(160, 10, 10, 0.24);
}

</style>
