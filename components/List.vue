<template>
  <div>
    <div class="bottom-space">
      <p>ID: {{ cocktail.idDrink }} | NAME: {{ cocktail.strDrink }}</p>
      <img
        :alt=cocktail.strDrink
        :src=cocktail.strDrinkThumb
      />
    </div>
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
h1 {
  margin-top: 3rem;
}
.bottom-space {
  margin-bottom: 3rem;
}
</style>
