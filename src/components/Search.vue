<template lang="html">
<div class="">
  <form>
    <input v-model="recipe"type="text" value="" placeholder="type a key word">
    <button type="button" @click="searchRecipe()">search</button>
  </form>
  <div v-for="recipe in recipes" class="main-div">
    <Recipe
      :title="recipe.title"
      :social_rank="recipe.social_rank"
      :image_url="recipe.image_url"
      :f2f_url="recipe.f2f_url"
      :publisher="recipe.publisher"
      />
  </div>
</div>
</template>

<script>
import axios from 'axios';
import Recipe from './Recipe.vue'
export default {
  name: "Search",
  components: {
    Recipe
  },
  data: () => ({
    recipes: [],
    recipe: ""
  }),
  methods: {
    searchRecipe() {
      axios.get(`https://www.food2fork.com/api/search?key=7003455ee7fd3683f2b5fea2e6ae90c0&q=${this.recipe} `)
        .then(response => response.data.recipes.map(recipe => {
          this.recipes.push({
            publisher: recipe.publisher,
            title: recipe.title,
            social_rank: recipe.social_rank,
            image_url: recipe.image_url,
            f2f_url: recipe.f2f_url
          })
        }))
    }
  }
}
</script>

<style lang="css" scoped>

.main-div {
border: 2px #d8412c solid;
margin: 5px;
}
input {
  width: 100px;
  border-radius: 3px;
  text-align: center;
  border: 2px solid #d8412c;
}
button {
  background-color: #d8412c
}
</style>
