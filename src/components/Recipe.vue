<template>
<div>
    
    <RecipePreview :recipe="recipe.recipePreview"></RecipePreview>
    {{RecipePreview}}

    <div class="div">
        <strong> Servings:</strong>
        <li v-on="recipe.servings"> {{recipe.servings}}</li>
        
    </div>
    <div class="div">
        <strong>Instructions:</strong>
        <ol>
        
          <!-- <li v-for="s in recipe.instructions" :key="s.number">{{ s.step }}</li> -->
        </ol>
    </div>

    <div class="div"><strong>Ingredients: </strong>

        <ul>
        <li v-for="(value, key,index) in recipe.ingredients"  :key="index">
         {{ key }}: {{ value }}
         </li>
        </ul>
        

    </div>



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