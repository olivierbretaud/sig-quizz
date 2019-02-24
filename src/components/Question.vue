<template>
	<div class="container-fluid d-flex flex-column justify-content-center align-items-center">
		<div class="question d-flex flex-column justify-content-center align-items-center">
			<h5 class="lora-bold" v-if="!displayAwnser">{{ questionData.id }} / 10</h5>  
			<h4 class="m-3 lora-bold" v-if="!displayAwnser" >{{ questionData.question }}</h4>
			<div class="button-container">
				<div v-for="response in questionData.responsesArray" v-bind:key="response">
					<button type="button" class="custom-button btn m-2 lora-bold" v-bind:class="{ 'd-none' : displayAwnser }" v-on:click="displayAwnser = true" @click="awnser(response, questionData.response )" > {{ response }} </button>
				</div>
			</div>
		</div>
		<div class="awnser anim d-flex flex-column justify-content-center align-items-center">
			<h4 class="m-3 lora-bold green" v-if="goodAwnser">Bravo!</h4>
			<h4 class="m-3 lora-bold red" v-if="badAwnser">Mauvaise réponse</h4>
			<h3 class="lora-bold" v-if="displayAwnser">{{ questionData.response }}</h3>  
			<h5 class="m-3" v-if="displayAwnser" >{{ questionData.description }}</h5>
			<a v-bind:href="questionData.next" class="js-scrollTo"><button type="button" class="custom-button btn lora-bold" v-if="displayAwnser">Question suivante</button></a>
		</div>
	</div>
</template>

<script>

export default {
	name: 'Question',
	props: {
		questionData: {},
	},
	data() {
		return {
			displayAwnser: false,
			goodAwnser: false,
			badAwnser: false,
		}
	},
	methods: {
		awnser(userResponse, response ) {
			if ( userResponse === response ) {
				this.$emit('count')
				this.goodAwnser  = true
			} else {
				this.badAwnser = true
			}
		}
	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container-fluid {
  min-height: 100vh;
  padding: 0;
}

.question {
	width: 100%;
	max-width: 600px;
	margin: 20px;
}

.awnser {
	width: 100%;
	max-width: 600px;
	margin: 20px;
	opacity: 1;
}

.anim {
  -moz-animation-name: main; /* Safari 4.0 - 8.0 */
  -moz-animation-duration: 2s; /* Safari 4.0 - 8.0 */
  animation-name: main;
  animation-duration: 2s;
}

/* Standard syntax */
@keyframes main {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.button-container {
	width: 100%;
	display: flex;
	flex-wrap: wrap;
	justify-content: center;
}

</style>