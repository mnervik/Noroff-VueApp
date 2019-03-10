<template>
    <div id="app">
        <Recipe :recipes="recipes"/>
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
                recipes: {
                    image: '',
                    title: '',
                    link: '',
                    ingredients: ''
                }
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

                        self.recipes.image = recipe.thumbnail;
                        self.recipes.title = recipe.title;
                        self.recipes.link = recipe.href;
                        self.recipes.ingredients = recipe.ingredients;
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
