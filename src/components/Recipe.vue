<template>
<div>
    
    <RecipePreview :recipe="recipe.recipePreview"></RecipePreview>
    {{RecipePreview}}

</div>

</template>
<script>
import RecipePreview from "../components/RecipePreview";
export default {
    components: {
        RecipePreview: RecipePreview
  },
props: {
        recipe: {
        type: Object,
        required: true
    }
},
methods:{
    async inFavorited(){
        this.axios.defaults.withCredentials = true;
        const response = await this.axios.get(
            // "http://isa-recipes.cs.bgu.ac.il/favorites",  
              // process.env.server_domain +"/favorites",
              "http://localhost:3000/users/favorites/",
                  );
        this.axios.defaults.withCredentials = false;

    }
}
}
    
</script>
<style>

</style>