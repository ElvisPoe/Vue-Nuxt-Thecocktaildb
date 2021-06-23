<template>
  <div class="cocktails-cards-container">
    <vs-row direction="row" justify="space-evenly">
      <Cocktail :key="index" :cocktail="cocktail" v-for="cocktail in this.cocktails" vs-type="flex" vs-justify="center" vs-align="center" w="12" />
    </vs-row>
  </div>
</template>


<script>
  export default {
    props: {
      cocktail: {
        type: Object
      }
    }
  }
</script>

<style scoped>

</style>
