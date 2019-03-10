<template>
    <div class="col">
        <div class="card" style="text-align: center">
            <img class="card-img-top" :src="image">
            <div class="card-body">
                <h5 class="card-title">{{title}}</h5>
                <p>LINK: <a :href="link">{{link}}</a></p>
                <p>{{ingredients}}</p>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['image', 'link', 'title', 'ingredients']
    }
</script>