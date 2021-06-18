<template>


  <vs-col vs-type="flex" vs-justify="center" vs-align="center" w="6">
    <div class="bottom-space">
      <p>ID: {{ cocktail.idDrink }} | NAME: {{ cocktail.strDrink }}</p>
      <img
        :alt=cocktail.strDrink
        :src=cocktail.strDrinkThumb
      />
    </div>
  </vs-col>

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
h1 {
  margin-top: 3rem;
}
.bottom-space {
  margin-bottom: 3rem;
}
</style>
