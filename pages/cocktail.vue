<template>
  <div class="container">

    <vs-card type="5">

      <template #title>
        <h3>{{ cocktailData.strDrink }}</h3>
      </template>

      <template #img>
        <img :src="cocktailData.strDrinkThumb" alt="">
      </template>

      <template #text>
        <p>{{ cocktailData.strInstructions }}</p>
      </template>

      <template #interactions>

        <vs-button info icon>
          <i class='bx bx-hash'></i>
          <span class="span">{{ cocktailData.idDrink }}</span>
        </vs-button>

        <vs-button v-if="cocktailData.strVideo" danger icon>
          <a :href="cocktailData.strVideo" class="icon-link" target="_blank">
            <i class='bx bxl-youtube'></i>
          </a>
        </vs-button>

        <vs-button info icon>
          <i class='bx bx-grid'></i>
          <span class="span">{{ cocktailData.strCategory }}</span>
        </vs-button>

        <vs-button danger>
          <span class="span">{{ cocktailData.strAlcoholic }}</span>
        </vs-button>

        <vs-button info icon>
          <i class='bx bx-hash'></i>
          <span class="span">{{ cocktailData.strGlass }}</span>
        </vs-button>

        <vs-tooltip right>
          <vs-button border>
            Ingredients
          </vs-button>
          <template #tooltip>
            <p v-if="cocktailData.strIngredient1">{{ cocktailData.strIngredient1 }} - {{ cocktailData.strMeasure1 }}</p>
            <p v-if="cocktailData.strIngredient2">{{ cocktailData.strIngredient2 }} - {{ cocktailData.strMeasure2 }}</p>
            <p v-if="cocktailData.strIngredient3">{{ cocktailData.strIngredient3 }} - {{ cocktailData.strMeasure3 }}</p>
            <p v-if="cocktailData.strIngredient4">{{ cocktailData.strIngredient4 }} - {{ cocktailData.strMeasure4 }}</p>
            <p v-if="cocktailData.strIngredient5">{{ cocktailData.strIngredient5 }} - {{ cocktailData.strMeasure5 }}</p>
            <p v-if="cocktailData.strIngredient6">{{ cocktailData.strIngredient6 }} - {{ cocktailData.strMeasure6 }}</p>
            <p v-if="cocktailData.strIngredient7">{{ cocktailData.strIngredient7 }} - {{ cocktailData.strMeasure7 }}</p>
            <p v-if="cocktailData.strIngredient8">{{ cocktailData.strIngredient8 }} - {{ cocktailData.strMeasure8 }}</p>
            <p v-if="cocktailData.strIngredient9">{{ cocktailData.strIngredient9 }} - {{ cocktailData.strMeasure9 }}</p>
            <p v-if="cocktailData.strIngredient10">{{ cocktailData.strIngredient10 }} - {{ cocktailData.strMeasure10 }}</p>
            <p v-if="cocktailData.strIngredient11">{{ cocktailData.strIngredient11 }} - {{ cocktailData.strMeasure11 }}</p>
            <p v-if="cocktailData.strIngredient12">{{ cocktailData.strIngredient12 }} - {{ cocktailData.strMeasure12 }}</p>
            <p v-if="cocktailData.strIngredient13">{{ cocktailData.strIngredient13 }} - {{ cocktailData.strMeasure13 }}</p>
            <p v-if="cocktailData.strIngredient14">{{ cocktailData.strIngredient14 }} - {{ cocktailData.strMeasure14 }}</p>
            <p v-if="cocktailData.strIngredient15">{{ cocktailData.strIngredient15 }} - {{ cocktailData.strMeasure15 }}</p>
          </template>
        </vs-tooltip>
      </template>
    </vs-card>

    <a href="/" class="icon-link mt-3">
      <vs-button info icon>
        <i class='bx bx-arrow-back'></i>
        <span class="span">Back</span>
      </vs-button>
    </a>
  </div>
</template>

<script>
export default {
  data() {
    return {
      cocktailData: [],
      cocktailId: ''
    }
  },

  // asyncData({ route }) {
  //   const id = route.query.id; // When calling /abc the slug will be "abc"
  //   return { id };
  // },

  beforeMount() {
    // get shop data
    this.cocktailId = this.$route.query.id;
  },

  async fetch() {
    var tempCocktailData = await fetch(
      `https://www.thecocktaildb.com/api/json/v1/1/lookup.php?i=${this.cocktailId}`
    ).then(
      (res) => res.json()
    )

    console.log(this.$route.query.id);
    console.log(this.$route);

    this.cocktailData = tempCocktailData.drinks[0];
  },

}
</script>
<style>
  .container {
    margin: 0 auto;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
  }
  .vs-card__interactions {
    width: 100%;
    justify-content: center;
  }
  .mt-3 {
   margin-top: 3rem;
  }
  a.icon-link {
    color: white;
    text-decoration: none;
  }
  .vs-card, .vs-card__img {
    width: 100%;
    max-width: 50vw;
    height: 60vh;
    max-height: 60vh;
    margin: auto;
  }
  .vs-card__img img {
    height: 100%;
    object-fit: cover;
    width: auto;
  }
</style>
