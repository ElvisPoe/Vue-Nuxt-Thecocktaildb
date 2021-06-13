<template>
  <div>
    <h1>Cocktails</h1>
    <p v-for="cocktail of cocktails">{{ cocktail }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      cocktails: [],
    }
  },
  async fetch() {
    this.cocktails = await fetch(
      'https://www.thecocktaildb.com/api/json/v1/1/list.php?i=list'
    ).then((res) => res.json())

    this.cocktailsByType = await fetch(
      'https://www.thecocktaildb.com/api/json/v1/1/filter.php?i=Gin'
    ).then((res) => res.json())

    ///https://www.thecocktaildb.com/api/json/v1/1/lookup.php?i=15300
  },
}
</script>
