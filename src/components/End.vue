<template>
  <div class="container-fluid d-flex flex-column justify-content-center align-items-center">
    <div class="end d-flex flex-column align-items-center">
      <h2 class="m-3 lora-bold" >{{ endSentence }}</h2>
      <div>
        <a href="#1" class="js-scrollTo"><button type="button" class="custom-button lora-bold btn m-2"> Revoir les réponses</button></a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'End',
  data() {
    return {
      endSentence: "Pour mettre fin aux inégalités en suisse, tou-te-s en grève le 14 juin!"
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