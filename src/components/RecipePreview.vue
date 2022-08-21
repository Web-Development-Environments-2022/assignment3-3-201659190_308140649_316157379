<template>
  
  <router-link
    :to="{ name: 'recipe', params: { recipeId: recipe.id } }"
<<<<<<< HEAD
    class="recipe-preview">
    <div :title="recipe.title" class="recipe-title">
       <h1> {{ recipe.title }}</h1>
    <div class="recipe-body">
      <!-- <img v-if="image_load" :src="recipe.image" class="recipe-image" /> -->
=======
    class="recipe-preview"
  >
    <h1>{{ recipe.title }}</h1>
    <div class="recipe-body" @mouseover="hover=true" @mouseleave="hover=false">
>>>>>>> d78f488140ec1c7d64d5dafd01ad2dca971be4ea
      <img :src="recipe.image" class="recipe-image" />
    </div>
<<<<<<< HEAD
    <!-- <div class="recipe-footer">
      <div :title="recipe.title" class="recipe-title">
        {{ recipe.title }}
      </div> -->
      <div :id="recipe.id" class="recipe-id">
        {{ recipe.id }}
      </div>
      <ul class="recipe-overview">
        <li>{{ recipe.readyInMinutes }} minutes</li>
        <li>{{ recipe.aggregateLikes }} likes</li>
        <li v-if="recipe.vegan">vegan</li>
        <li v-if="recipe.vegetarian">vegetarian</li>
        <li v-if="recipe.glutenFree">gluten free</li>
      </ul>
    </div>
=======
      <div class="recipe-footer">
        <div :id="recipe.id" class="recipe-id">
          {{ recipe.id }}
        </div>
        <ul class="recipe-overview">
          <li>{{ recipe.readyInMinutes }} minutes</li>
          <li>{{ recipe.aggregateLikes }} likes</li>
          <li v-if="recipe.vegan">vegan</li>
          <li v-if="recipe.vegetarian">vegetarian</li>
          <li v-if="recipe.glutenFree">gluten free</li>
        </ul>
      </div>
>>>>>>> d78f488140ec1c7d64d5dafd01ad2dca971be4ea
  </router-link>
</template>

<script>

export default {

  data() {
    return {
<<<<<<< HEAD
      // image_load: false
=======
      hover: false,
>>>>>>> d78f488140ec1c7d64d5dafd01ad2dca971be4ea
    };
  },
  props: {
    recipe: {
      type: Object,
      required: true
    },
<<<<<<< HEAD

    // id: {
    //   type: Number,
    //   required: true
    // },
    // title: {
    //   type: String,
    //   required: true
    // },
    // readyInMinutes: {
    //   type: Number,
    //   required: true
    // },
    // image: {
    //   type: String,
    //   required: true
    // },
    // aggregateLikes: {
    //   type: Number,
    //   required: false,
    //   default() {
    //     return undefined;
    //   }
    // }
  }
=======
  },
>>>>>>> d78f488140ec1c7d64d5dafd01ad2dca971be4ea
};
</script>

<style scoped>
.recipe-preview {
  display: inline-block;
  width: 90%;
  height: 100%;
  position: relative;
  margin: 10px 10px;
}
/* .recipe-preview > .recipe-body {
  width: 100%;
  height: 200px;
  position: relative;
} */

/* .recipe-preview .recipe-body .recipe-image {
  margin-left: auto;
  margin-right: auto;
  margin-top: auto;
  margin-bottom: auto;
  display: block;
  width: 98%;
  height: auto;
  -webkit-background-size: cover;
  -moz-background-size: cover;
  background-size: cover;
} */


.recipe-image {
  border: 1px solid #ddd;
  border-radius: 4px;
  padding: 5px;
  width: 150px;
}

.recipe-image:hover {
  box-shadow: 0 0 2px 1px rgba(0, 140, 186, 0.5);
}


.recipe-preview .recipe-footer {
  width: 100%;
  height: 50%;
  overflow: hidden;
}

.recipe-preview .recipe-footer .recipe-title {
  padding: 10px 10px;
  width: 100%;
  font-size: 12pt;
  text-align: left;
  white-space: nowrap;
  overflow: hidden;
  -o-text-overflow: ellipsis;
  text-overflow: ellipsis;
}
/* 
.recipe-preview .recipe-footer ul.recipe-overview {
  padding: 5px 10px;
  width: 100%;
  display: -webkit-box;
  display: -moz-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  -o-box-flex: 1;
  box-flex: 1;
  -webkit-flex: 1 auto;
  -ms-flex: 1 auto;
  flex: 1 auto;
  table-layout: fixed;
  margin-bottom: 0px;
} */



/* .recipe-preview .recipe-footer ul.recipe-overview li {
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  -o-box-flex: 1;
  -ms-box-flex: 1;
  box-flex: 1;
  -webkit-flex-grow: 1;
  flex-grow: 1;
  width: 90px;
  display: table-cell;
  text-align: center;
}  */
</style>
