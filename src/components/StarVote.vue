<template>
    <div>
        <font-awesome-icon class="vote" icon="star" v-for="(num, i) in newVote" :key="i"/>
    </div>
</template>

<script>
import { library } from '@fortawesome/fontawesome-svg-core'
import { faStar } from '@fortawesome/free-solid-svg-icons'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'

library.add(faStar);

export default {
    components:{
        FontAwesomeIcon,
    },
    props:{
        vote: Number
    },
    computed:{
        newVote(){
            const fiveVote = Math.round((this.vote / 2));
            return fiveVote;
        }
    }
    
}
</script>

<style lang="scss" scoped>
.vote{
    color: goldenrod;
}
</style>