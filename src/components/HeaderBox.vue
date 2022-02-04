<template>
    <div class="header">
        <div>
            <h1 @click="homeClick">Boolflix</h1>
            <p :class="newHomeBool ? 'clicked':''" @click="homeClick">Home</p>
            <p :class="newSerieBool ? 'clicked':''" @click="serieClick">Serie TV</p>
            <p :class="newFilmBool ? 'clicked':''" @click="filmClick">Film</p>
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
    props:{
        newHomeBool: Boolean,
        newSerieBool: Boolean,
        newFilmBool: Boolean,
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
            cursor: pointer;
        }
    
        p{
            color: white;
            margin-right: 0;
            padding: 0 10px;
            transition: all 0.5s;

            &:hover{
                cursor: pointer;
                border-bottom: 2px solid red;
                padding-bottom: 4px;
                font-weight: bold;
                font-size: 18px;
                transition: all 0.5s;
            }
        }

        .clicked{
            border-bottom: 2px solid red;
            padding-bottom: 4px;
            font-weight: bold;
            font-size: 18px;
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