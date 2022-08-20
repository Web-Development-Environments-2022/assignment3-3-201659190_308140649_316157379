<template>
  <div class="container">
    <h1 class="title">Main Page</h1>
    <b-row>
      <b-col>
        <RecipePreviewList title="Randome Recipes" class="RandomRecipes center" ></RecipePreviewList> 
        <b-button id="btnRandomRecipes" variant="primary" @click="changeRandomRecipe">Change recipe</b-button> 
      </b-col>
      <b-col>
        <router-link v-if="!$root.store.username" to="/login" tag="button">You need to Login to vue this</router-link>
        <RecipePreviewListLestSeen
          title="Last Viewed Recipes"
          :class="{
            RandomRecipes: True,
            blur: !$root.store.username,
            center: true
          }"
          id="laseSeenRecipt"
          disabled
        ></RecipePreviewListLestSeen >
      </b-col>
    </b-row>
    
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
  margin-top: 5vh;
}

#btnRandomRecipes{
  margin-top: 2vh;
  margin-bottom: 5vh;
}

#laseSeenRecipt{
  margin-top: 5vh;
  width: 80%;
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
