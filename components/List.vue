<template>
  <div>
    <div>
      <h1>Ingredients</h1>
      <button @click="collectData">Get Data</button>
      <p v-for="ingredient of ingredients['drinks']">{{ ingredient.strIngredient1 }}</p>
    </div>

    <div>
      <h1>Cocktails</h1>
      <p v-for="cocktail of cocktailsByType">
        {{ cocktail }}
      </p>
    </div>

  </div>
</template>

<script>
export default {

  data() {
    return {
      ingredients: [],
      cocktailsByType: [],
    }
  },

  created(){
    var inputData = fetch('https://www.thecocktaildb.com/api/json/v1/1/list.php?i=list')

    console.log(inputData)
    // console.log(JSON.stringify(inputData))
    // console.log(';)')
  },

  methods: {
    collectData() {
      var ingredientsJson = fetch(
        'https://www.thecocktaildb.com/api/json/v1/1/list.php?i=list'
      )
      this.ingredients = ingredientsJson;
    },
  },

  /*async fetch() {
    this.ingredients = await fetch(
      'https://www.thecocktaildb.com/api/json/v1/1/list.php?i=list'
    ).then((res) => res.json())

    this.cocktailsByType = await fetch(
      'https://www.thecocktaildb.com/api/json/v1/1/filter.php?i=Egg yolk'
    ).then((res) => res.json())

    ///https://www.thecocktaildb.com/api/json/v1/1/lookup.php?i=15300
  },*/
}
</script>
