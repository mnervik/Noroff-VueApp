<template>
    <div class="col">
        <div class="card" style="text-align: center">
            <img class="card-img-top" :src="recipes.image">
            <div class="card-body">
                <h5 class="card-title">{{recipes.title}}</h5>
                <p>LINK: <a :href="recipes.link">{{recipes.link}}</a></p>
                <p>{{recipes.ingredients}}</p>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['recipes']
    }
</script>