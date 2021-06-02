<template>
<h1>Movie info</h1>
    <div v-for="(item, index) in movieDetails" v-bind:key="index">
        <img :src="item.Poster" alt="">
        <div>Title: {{ item.Title }} </div>
        <div>Year: {{ item.Year }} </div>
        <hr>
    </div>
</template>

<script>
export default {
    name: "movieList", 
    props: {
        movieDetails: Array
    }
}
</script>