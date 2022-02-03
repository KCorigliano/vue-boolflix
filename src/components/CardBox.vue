<template>
    <div class="card-container">
        <p>Titolo: {{title}}</p>
        <p>Titolo originale: {{originalTitle}}</p>
        <p>Voto: {{vote}}</p>
        <p>Overview: {{overview}}</p>
    </div>
</template>

<script>
export default {
    props:{
        title: String,
        originalTitle: String,
        vote: String,
        overview: String,
    }
}
</script>

<style lang="scss" scoped>
.card-container{
    width: calc(100% / 5);
    margin: 0 15px 0 0;
}
</style>