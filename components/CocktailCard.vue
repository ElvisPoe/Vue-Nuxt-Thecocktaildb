<template>
  <NuxtLink prefetch class="card-link" :to="{ name: 'cocktail', query: { id: cocktail.idDrink } }">
    <vs-card type="1" class="mb-1-5">

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
  </Nuxtlink>
</template>

<script>
export default {
  data() {
    return {
      cocktailData: []
    }
  },

  methods: {
    showCocktail(cocktail) {
      this.$router.push({path: `/cocktail?id=${cocktail.idDrink}`})
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
