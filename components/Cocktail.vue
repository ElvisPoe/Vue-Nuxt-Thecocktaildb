<template>
  <vs-card type="1" class="mb-1-5" @click="showCocktail(cocktail)">

    <template #title>
      <h3> {{ cocktail.strDrink }}</h3>
    </template>

    <template #img>
      <img :src=cocktail.strDrinkThumb :alt=cocktail.strDrink>
    </template>

    <template #text>
      <p>
        # {{ cocktail.idDrink }}
      </p>
    </template>

  </vs-card>
</template>

<script>
export default {
  data() {
    return {
      cocktailData: []
    }
  },

  methods: {
    async showCocktail(cocktail) {
        this.cocktailData = await fetch(
          `https://www.thecocktaildb.com/api/json/v1/1/lookup.php?i=${cocktail.idDrink}`
        ).then(
          (res) => res.json()
        )
      this.$router.push ({name: 'cocktail', params: {cocktailData: this.cocktailData.drinks[0]}})

    }
  },

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
.mb-1-5 {
  margin-bottom: 1.5rem;
}
</style>
