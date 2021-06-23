<template>
  <div class="center examplex">
    <vs-navbar center-collapsed v-model="active">

      <template #left>
        <a href="/">
          <img src="https://www.thecocktaildb.com/images/logo.png" alt="">
        </a>
      </template>

      <vs-select placeholder="Select" v-model="value" v-on:change="getCocktails(value)">
        <vs-option v-for="ingredient of ingredients['drinks']" :label="ingredient.strIngredient1" :value="ingredient.strIngredient1">
          {{ ingredient.strIngredient1 }}
        </vs-option>
      </vs-select>

      <template #right>
        <vs-button>Get Started</vs-button>
        <vs-avatar primary badge badge-color="success">
          <i class='bx bxs-hot' ></i>
        </vs-avatar>
      </template>
    </vs-navbar>

    <div class="cocktails-cards-container">
      <vs-row direction="row" justify="space-evenly">
        <Cocktail :key="index" :cocktail="cocktail" v-for="cocktail in this.cocktails.drinks" vs-type="flex" vs-justify="center" vs-align="center" w="12" />
      </vs-row>
    </div>

  </div>
</template>

<script>
  export default {

    data() {
      return {
        value: '',
        ingredients: [],
        cocktails: [],
      }
    },

    created(){
      this.cocktails = fetch(
        'https://www.thecocktaildb.com/api/json/v1/1/filter.php?i=Gin'
      ).then(
        (res) => res.json()
      )
    },

    async fetch() {
      this.ingredients = await fetch(
        'https://www.thecocktaildb.com/api/json/v1/1/list.php?i=list'
      ).then(
        (res) => res.json()
      )
    },

    methods: {
      async getCocktails(value) {
        this.cocktails = await fetch(
          `https://www.thecocktaildb.com/api/json/v1/1/filter.php?i=${value}`
        ).then(
          // store.commit('cocktailsList', res.json())
          (res) => res.json()
        )
      },
    },

  }
</script>

<style scoped>
  .vs-navbar-content {
    padding: 15px;
  }

  .cocktails-cards-container {
    margin-top: 5rem;
    width: 100vw;
  }
</style>
