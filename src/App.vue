<template>
    <div id="app">
        <Recipe :image="recipeImg" :title="recipeTitle" :link="recipeLink" :ingredients="recipeIngredients"/>
    </div>
</template>

<script>
    import Recipe from './components/Recipe.vue'
    import axios from 'axios'

    export default {
        name: 'app',
        components: {
            Recipe
        },
        data() {
            return {
                recipeImg: '',
                recipeTitle: '',
                recipeLink: '',
                recipeIngredients: ''
            }
        },
        created: function () {
            this.fetchRecipes();
        },
        methods: {
            fetchRecipes: function () {
                let self = this;
                let url = 'http://www.recipepuppy.com/api/';
                axios.get(url)
                    .then(function (result) {
                        let recipe = result.data.results[0];

                        /* Set Data */
                        self.recipeImg = recipe.thumbnail;
                        self.recipeTitle = recipe.title;
                        self.recipeLink = recipe.href;
                        self.recipeIngredients = recipe.ingredients;
                    });
            }
        }
    }
</script>

<style>
    [v-cloak] {
        display: none;
    }
</style>
