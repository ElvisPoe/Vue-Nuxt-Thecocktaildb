<template lang="html">
  <div class="centerx icons-example">
    <div>
      <h1>Ingredients</h1>
      <vs-select placeholder="Select" v-model="value" v-on:change="getCocktail(value)">
        <vs-option v-for="ingredient of ingredients['drinks']" :label="ingredient.strIngredient1" :value="ingredient.strIngredient1">
          {{ ingredient.strIngredient1 }}
        </vs-option>
      </vs-select>
    </div>

    <List v-for="cocktail in this.cocktails.drinks" :cocktail="cocktail" />

  </div>
</template>

<script>
import List from '~/components/List.vue'

export default {
  data() {
    return {
      value: '',
      ingredients: [],
      cocktails: [],
    }
  },

  components: {
    List
  },

  async fetch() {
    this.ingredients = await fetch(
      'https://www.thecocktaildb.com/api/json/v1/1/list.php?i=list'
    ).then((res) => res.json())

    ///https://www.thecocktaildb.com/api/json/v1/1/lookup.php?i=15300
  },

  methods: {
    async getCocktail(value) {
      this.cocktails = await fetch(
        `https://www.thecocktaildb.com/api/json/v1/1/filter.php?i=${value}`
      ).then((res) => res.json())

      // console.log(this.cocktails.drinks);
    }
  },

}
</script>

<style scoped>
  h1 {
    margin-bottom: 3rem;
  }
</style>
