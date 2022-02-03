<template>
    <div class="header">
        <h1>Boolflix</h1>
        <div>
            <input type="text" placeholder="Cerca un film">
            <button>Search</button>
        </div>
    </div>
</template>

<script>
export default {
    
}
</script>

<style lang="scss" scoped>
.header{
    background-color: black;
    display: flex;
    justify-content: space-between;
    width: 100%;
    align-items: center;
    padding: 0 15px;
    height: 50px;

    h1{
        color: red;
        text-transform: uppercase;
    }

    div{
        input{
            margin-right: 15px;
        }
    }
}
</style>