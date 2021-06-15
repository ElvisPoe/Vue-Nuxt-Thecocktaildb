<template lang="html">
  <div class="centerx icons-example">
    <div>
      <h1>Ingredients</h1>
      <vs-select placeholder="Select" v-model="value" v-on:change="ingredientSelected(value)">
        <vs-option v-for="ingredient of ingredients['drinks']" :label="ingredient.strIngredient1" :value="ingredient.strIngredient1">
          {{ ingredient.strIngredient1 }}
        </vs-option>
      </vs-select>
    </div>

    <List @cocktails="this.cocktails" />

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

  methods: {
    async ingredientSelected(value) {
      this.cocktails = await fetch(
        'https://www.thecocktaildb.com/api/json/v1/1/filter.php?i=' + value
      ).then((res) => res.json())

      console.log(this.cocktails.drinks);
    }
  },

  async fetch() {
    this.ingredients = await fetch(
      'https://www.thecocktaildb.com/api/json/v1/1/list.php?i=list'
    ).then((res) => res.json())

    // this.cocktailsByType = await fetch(
    //   'https://www.thecocktaildb.com/api/json/v1/1/filter.php?i=Egg yolk'
    // ).then((res) => res.json())

    ///https://www.thecocktaildb.com/api/json/v1/1/lookup.php?i=15300
  },
}
</script>

<style scoped>

</style>
