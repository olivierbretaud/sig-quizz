<template>
	<div class="container-fluid d-flex flex-column justify-content-center align-items-center top">
		<div v-if="!displayAwnser" class="question d-flex flex-column justify-content-center align-items-center">
			<h5 class="lora-bold" v-if="!displayAwnser">{{ questionData.id }} / 10</h5>  
			<h4 class="m-3 lora-bold" v-if="!displayAwnser" >{{ questionData.question }}</h4>
			<div class="button-container">
				<div v-for="response in questionData.responsesArray" v-bind:key="response">
					<button type="button" class="custom-button btn m-2 lora-bold" v-bind:class="{ 'd-none' : displayAwnser }" @click="awnser(response, questionData.response )" > {{ response }} </button>
				</div>
			</div>
		</div>
		<transition name="slide-fade">
			<div v-if="displayAwnser" class="awnser d-flex flex-column justify-content-center align-items-center">
				<h4 class="mb-3 lora-bold green" v-if="goodAwnser">Bravo!</h4>
				<h4 class="mb-3 lora-bold red" v-if="badAwnser">Mauvaise réponse</h4>
				<h4 class="lora-bold">{{ questionData.response }}</h4>  
				<h5 class="m-3" >{{ questionData.description }}</h5>
				<a v-bind:href="questionData.next" v-smooth-scroll >
					<button type="button" class="custom-button btn lora-bold" v-if="questionData.next">{{ nextQuestion }}</button></a>
			</div>
		</transition>
		<div class="progress">
			<div class="progress-bar bg-progress" role="progressbar" v-bind:style="{width: progress + '%'} "  aria-valuemin="0" aria-valuemax="10"></div>
		</div>
	</div>
</template>

<script>

export default {
	name: 'Question',
	props: {
		questionData: Object,
		progress: Number
	},
	data() {
		return {
			nextQuestion: "Question suivante",
			displayAwnser: false,
			goodAwnser: false,
			badAwnser: false,
		}
	},
	created: function () {
		if (this.questionData.next === "#end") {
			this.nextQuestion = "Découvrez votre score"
		}
	},
	methods: {
		awnser(userResponse, response ) {
			this.$emit('progress')
			if ( userResponse === response ) {
				this.$emit('count')
				this.displayAwnser = true
				this.goodAwnser  = true
			} else {
				this.displayAwnser = true
				this.badAwnser = true
			}
		}
	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.question {
	width: 100%;
	max-width: 600px;
    padding: 20px;
	padding-bottom: 30px;
}

.awnser {
	width: 100%;
	max-width: 600px;
    padding: 20px;
	padding-bottom: 30px;
}

.bg-progress {
	height: 100px;
	background-color: #05A0DF !important;
}

.slide-fade-enter-active {
  transition: all .3s ease;
}
.slide-fade-leave-active {
  transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateX(100px);
  opacity: 0;
}

.button-container {
	width: 100%;
	display: flex;
	flex-wrap: wrap;
	justify-content: center;
}

</style>