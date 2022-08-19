<template>
    <div>
     <!-- need to complete validation and fix instruction and ingredients to be multiple input that controledby user -->
    <b-modal id="recipeCreation" title="Create new recipe" @show="resetModal" @hidden="resetModal" hide-footer>
      <b-form-group label="Enter recipe title" label-for="recipeTitle" >
        <b-form-input id="recipeTitle" v-model="recipe.title" :state="recipeTitleState"></b-form-input>
        <b-form-invalid-feedback>
            Enter at least 1 letters
        </b-form-invalid-feedback>
      </b-form-group>
       <b-form-group label="Add image URL" label-for="recipeImage">
        <b-form-input id="recipeImage" v-model="recipe.image" :state="recipeImageState"></b-form-input>
        <b-form-invalid-feedback>
            Enter image url
        </b-form-invalid-feedback>
      </b-form-group>
       <b-form-group label="Enter recipe's time preperation" label-for="recipeTimePreperation">
        <b-form-input id="recipeTimePreperation" v-model="recipe.timePreperation" :state="recipeTimePreperationState"></b-form-input>
        <b-form-invalid-feedback>
            Enter at least 1 digit
        </b-form-invalid-feedback>
      </b-form-group>
      <b-form-group label="Enter recipe's serving amount" label-for="recipeServing">
        <b-form-input id="recipeServing" v-model="recipe.serving" :state="recipeServingState"></b-form-input>
        <b-form-invalid-feedback>
            Enter at least 1 digit
        </b-form-invalid-feedback>
      </b-form-group>

      <b-form-group>
        <div v-for="(instructionStep, i) in recipe.instructions" :key="i">
          Add instruction:
          <b-form-input v-model="instructionStep.instruction" placeholder="Instruction"></b-form-input>
          <br>
        </div>
        <b-button type="button" @click="addNewInstruction">Add instruction</b-button>
      </b-form-group>

      <b-form-group >
        <div v-for="(ingredientStep, i) in recipe.ingredients" :key="i">
          Add ingredient:
          <b-form-input v-model="ingredientStep.ingredient" placeholder="ingredient" ></b-form-input>
          <b-form-input v-model="ingredientStep.amount" placeholder="amount" required></b-form-input>
          <br>
        </div>
        <b-button type="button" @click="addNewIngredient">Add Ingredient</b-button>
      </b-form-group>
      <b-form-checkbox-group v-model="selected" :options="options" value-field="item" text-field="name">
      </b-form-checkbox-group>
      <b-form-group >
        <b-button id="btnSubmit" variant="primary">Submit</b-button>
        <b-button id="btnCancel" variant="secondary" @click="$bvModal.hide('recipeCreation')">Cancel</b-button>
      </b-form-group>

    </b-modal>
    </div>
</template>

<script>
import { required } from "vuelidate/lib/validators";
export default {
  name: "createRecipeModel",
  data(){
    return{
      recipe:{
        title:'',
        selected:[],
        options:[
          {item: 'Vegan', name: 'Vegan'},
          {item: 'Gluten', name: 'Gluten'}
        ],
        image: '',
        timePreperation: '',
        ingredients: [{
          ingredient:'',
          amount:'',
        }],
        instructions: [{
          instruction:'test',
        }],
        serving: '',
      }
    }
  },
  validations: {
    recipe: {
      title: {
        required
      },
      image: {
        required
      },
      timePreperation: {
        required
      },
      ingredients: {
        ingredient:{
          required
        },
        amount:{
          required
        }
      },
      instructions:{
        instruction:{
          required
        }
      }
    },
  },
  computed:{
    recipeTitleState(){
        return this.recipe.title.length === 0 ? false : true;
    },
    recipeImageState(){
        return this.recipe.image.length === 0 ? false : true;
    },
    recipeTimePreperationState(){
        return this.recipe.timePreperation.length === 0 ? false : true;
    },
    recipeServingState(){
        return this.recipe.serving.length === 0 ? false : true;
    },
    // recipeInstructionsState(){
    //   return true;
    //   return this.recipe.instructions[instruction].length === 0 ? false : true;
    // },
    // recipeIgrediantsState(){
    //   return true;
    //   return this.recipe.ingredients.ingredients.length === 0 ||
    //           this.recipe.ingrediants.amount.length === 0 ? false : true;
    // }
  },
  methods: {
    Logout() {
      this.$root.store.logout();
      this.$root.toast("Logout", "User logged out successfully", "success");

      this.$router.push("/").catch(() => {
        this.$forceUpdate();
      });
    },
    resetModal(){
      this.recipe.title = '';
      this.recipe.selected = [];
      this.recipe.image = '';
      this.recipe.timePreperation = '';
      this.recipe.ingredients= [{
        ingredient:'',
        amount:'',
      }];
      this.recipe.instructions= [{
        instruction:'',
      }];
      this.recipe.serving= '';
    },
    // need to delete the session check in the end
    async handleSubmit(){
      const session = this.$cookies.get("session");
      if(session){
            const response = await this.axios.get(this.$store.server_domain + "/users/my_recipe",
            {
              recipe: this.recipe,
            },
            {
              withCredentials: true,
            }
      )}
      else{
        alert("no cookies, need to re-login");
      }
    },
    addNewInstruction(){
      this.recipe.instructions.push({
        instruction: '',
      });

    },
    addNewIngredient(){
      this.recipe.ingredients.push({
        ingredient:'',
        amount:'',
      })
    }
  }
};
</script>
<style>
  #btnSubmit{
    margin-left: 15vh;


  }
  #btnCancel{
   margin-left: 5vh;
  }
</style>