<template>
 <div>
      <Recipe class="center" :recipe="recipeData" />



 </div>
</template>

<script>
import Recipe from "../components/Recipe";
export default {
  components: {
    Recipe: Recipe
  },
  data() {
    return {
      recipeData: {
        type: Object,
        require: true
      }
    };
  },
  async mounted() {
    try {
      let response;
      // response = this.$route.params.response;

      try {
        response = await this.axios.get(
          // "https://test-for-3-2.herokuapp.com/recipes/info",
          this.$store.server_domain + "/recipes/638808/details",
          // "http://isa-recipes.cs.bgu.ac.il/recipes/638808/details",
          //  process.env.server_domain + "recipes/638808/details",
            // "http://localhost:3000/recipes/638808/details",
          // {
          //   params: { id: this.$route.params.recipeId }
          // },
          {
            withCredentials: true
          }
        );

        // console.log("response.status", response.status);
        if (response.status !== 200) this.$router.replace("/NotFound");
      } catch (error) {
        console.log("error.response.status", error.response.status);
        this.$router.replace("/NotFound");
        return;
      }
      let {
        instructions,
        servings,
        ingredients,
        recipePreview,
      } = response.data;
      // alert(response.data)
      this.recipeData = response.data;
      // alert(response.data.instructions);




      // let _instructions = analyzedInstructions
      //   .map((fstep) => {
      //     fstep.steps[0].step = fstep.name + fstep.steps[0].step;
      //     return fstep.steps;
      //   })
      //   .reduce((a, b) => [...a, ...b], []);

      // let _recipe = {
      //   id,
      //   instructions,
      //   _instructions,
      //   // analyzedInstructions,
      //   extendedIngredients,
      //   aggregateLikes,
      //   readyInMinutes,
      //   image,
      //   title,
      //   vegan,
      //   glutenFree,
      // };

      // this.recipe = _recipe;
    } catch (error) {
      console.log(error);
    }
  }

};
</script>

<style scoped>
.wrapper {
  display: flex;
}
.wrapped {
  width: 50%;
}
.center {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 50%;
}
/* .recipe-header{

} */
</style>