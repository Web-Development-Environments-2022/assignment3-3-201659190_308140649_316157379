<template>
  <div class="container">
    <h1 class="title">Main Page</h1>
    <b-button variant="primary" @click="changeRandomRecipe">Change recipe</b-button>
    <RecipePreviewList title="Randome Recipes" class="RandomRecipes center" ></RecipePreviewList>  
    <router-link v-if="!$root.store.username" to="/login" tag="button">You need to Login to vue this</router-link>
    <RecipePreviewListLestSeen
      title="Last Viewed Recipes"
      :class="{
        RandomRecipes: True,
        blur: !$root.store.username,
        center: true
      }"
      disabled
    ></RecipePreviewListLestSeen>
    <!-- <div
      style="position: absolute;top: 70%;left: 50%;transform: translate(-50%, -50%);"
    >
      Centeredasdasdad
    </div>-->
  </div>
</template>

<script>

import RecipePreviewList from "../components/RecipePreviewList";
import RecipePreviewListLestSeen from "../components/RecipePreviewListLestSeen";
export default {
  components: {
    RecipePreviewList, RecipePreviewListLestSeen
  },
  methods:{
    //need to complete this function
    changeRandomRecipe(){
      alert('need to complete this function')
    }
  }
};

</script>

<style lang="scss" scoped>
.RandomRecipes {
  margin: 10px 0 10px;
}
.blur {
  -webkit-filter: blur(5px); /* Safari 6.0 - 9.0 */
  filter: blur(5px);
}
::v-deep .blur .recipe-preview {
  pointer-events: none;
  cursor: default;
}
</style>
