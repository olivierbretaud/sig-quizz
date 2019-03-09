<template>
	<div class="container-fluid d-flex flex-column justify-content-center align-items-center">
		<div class="end d-flex flex-column align-items-center">
			<h3 class="m-3 mt-0 lora-bold red">Vous avez {{ totalCount }}% de bonnes réponses </h3>
			<h5 class="m-3" >{{ getResultSentence }}</h5>
			<div>
				<a href="#1" v-smooth-scroll="{ duration: 1000, offset: -50 }">
					<button type="button" class="custom-button lora-bold btn m-2"> Revoir les réponses</button>
				</a>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: 'Result',
	props: {
		totalCount: Number
	},
	data() {
		return {
			resultSentence: "",
		}
    },
     computed: {
        getResultSentence: function () {
            let resultSentence =""
            if (this.totalCount < 25 ) {
                resultSentence = "Vous idéalisez la situation des femmes en Suisse ! Il nous reste encore beaucoup de chemin à faire pour parvenir à l’égalité ! Le 14 juin, rejoignez-nous, faites la grève pour faire avancer l’égalité entre femmes et hommes en Suisse !";
            }
            else if (this.totalCount > 25 && this.totalCount < 75 ) {
                resultSentence = "vous êtes une féministe en devenir mais la route est encore longue jusqu'à l'égalité entre hommes et femmes. Rencontrons nous le 14 juin pour améliorer la situation des Femmes!";
            }
            else {
                resultSentence = "Bravo, vos connaissances sont presque complètes mais l'égalité n'est pas encore au tournant, vos efforts importent donc n'hésitez pas à militer partout ou vous passez! Et c'est certain, nous nous croisons le 14 juin!";
            }
            return resultSentence
        }
	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.end {
  max-width: 600px;
  margin: 10px;
}

</style>