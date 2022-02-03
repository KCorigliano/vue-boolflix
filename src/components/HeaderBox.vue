<template>
    <div class="header">
        <div>
            <h1>Boolflix</h1>
            <p>Home</p>
            <p>Serie TV</p>
            <p>Film</p>
            <p>Originali</p>
            <p>Aggiunti di recente</p>
            <p>La mia lista</p>
        </div>
        <div>
            <input type="text" v-model="filmTitle" placeholder="Cerca un film" @keyup.enter="searchFilm">
            <button @click="searchFilm">Search</button>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            filmTitle: '',
            search: false,
        }
    },
    methods: {
        searchFilm(){
            this.$emit('searchFilm', this.filmTitle);
        }
    },
}
</script>

<style lang="scss" scoped>
.header{
    display: flex;
    justify-content: space-between;
    width: 100%;
    align-items: center;
    padding: 0 15px;
    height: 50px;

    div:first-child{
        display: flex;
        align-items: center;

        h1{
            color: red;
            text-transform: uppercase;
            margin-right: 50px;
        }
    
        p{
            color: white;
            margin-right: 30px;

            &:hover{
                cursor: pointer;
                color: red;
            }
        }
    }

    div{
        input{
            margin: 0 15px;
        }

        button{
            cursor: pointer;
        }
    }
}
</style>