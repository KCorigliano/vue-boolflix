<template>
    <div class="header">
        <div>
            <h1>Boolflix</h1>
            <p @click="homeClick">Home</p>
            <p @click="serieClick">Serie TV</p>
            <p @click="filmClick">Film</p>
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
            homeBool: true,
            serieBool: false,
            filmBool: false,
        }
    },
    methods: {
        searchFilm(){
            this.$emit('searchFilm', this.filmTitle);
        },
        homeClick(){
            this.$emit('homeClick', this.homeBool, this.serieBool, this.filmBool)
        },
        serieClick(){
            this.$emit('serieClick', this.homeBool, this.serieBool, this.filmBool)
        },
        filmClick(){
            this.$emit('filmClick', this.homeBool, this.serieBool, this.filmBool)
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