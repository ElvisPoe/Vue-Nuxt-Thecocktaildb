<template>
  <div>
    <div>
      <h1>Cocktails</h1>
      <p v-for="cocktail of cocktails">
        {{ cocktail }}
      </p>
    </div>

  </div>
</template>

<script>
export default {

  data() {
    return {
      cocktails: this.cocktails,
    }
  },

  created(){
    // var inputData = fetch('https://www.thecocktaildb.com/api/json/v1/1/list.php?i=list')
    // console.log(inputData)
    // console.log(JSON.stringify(inputData))
    // console.log(';)')
  },

  methods: {
    collectData() {

    },
  },

  async fetch() {
      this.cocktailsByType = await fetch(
        'https://www.thecocktaildb.com/api/json/v1/1/filter.php?i=Egg yolk'
      ).then((res) => res.json())

      ///https://www.thecocktaildb.com/api/json/v1/1/lookup.php?i=15300
    },
  }
</script>
