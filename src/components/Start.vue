<template>
	<div class="container-fluid d-flex flex-column justify-content-center align-items-center">
		<div class="intro d-flex flex-column align-items-center">
			<h1 class="lora-bold">Quizz égalité</h1>
			<h5 class="m-3" >{{ startSentence }}</h5>
			<div>
				<a href="#1" v-smooth-scroll="{ duration: 1000, offset: -50 }"><button type="button" class="custom-button lora-bold btn m-2"> Démarrer le quizz ! </button></a>
			</div>
		</div>
		<img src="../assets/logo-sit.svg" class="logo-sit"/>
	</div>
</template>

<script>
export default {
  name: 'Start',
  data() {
    return {
      startSentence: "Testez vos connaissances sur l’égalité entre femmes et hommes en Suisse"
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.intro {
	max-width: 400px;
	margin-top: 30px;
	margin: 10px;
}

.logo-sit {
	width: 200px;
	height: 200px;
	object-fit: cover;
}

</style>