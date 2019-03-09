<template>
	<div class="container-fluid d-flex flex-column justify-content-center align-items-center">
		<div class="end d-flex flex-column align-items-center">
			<img src="../assets/logo-manif.png" class="logo-manif"/>
			<h3 class="m-3 lora-bold" >{{ endSentence }}</h3>
			<div>
				<a href="#result" v-smooth-scroll="{ duration: 1000, offset: -50 }">
					<button type="button" class="custom-button lora-bold btn m-2">Découvrez votre score</button>
				</a>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: 'End',
	props: {
		totalCount: Number
	},

	data() {
		return {
			endSentence: "Pour mettre fin aux inégalités en suisse, tou-te-s en grève le 14 juin!"
		}
	},

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.end {
  max-width: 600px;
  margin: 10px;
}

.logo-manif {
	width: 200px;
	height: 200px;
	object-fit: contain;
}

</style>