<template>
    <div class="player" @mousedown="mousedown">
        </div>  
</template>

<script>

export default {
    name: 'Player',
    props:{
        player_side: String,
    },
    data(){
        return{
            pos1: 0,
            pos2: 0,
            pos3: 0,
            pos4: 0,
            
        }
    },
    methods:{
        mousedown(event){
            
            this.$emit('playerTouched',event,this.player_side)
        }
    },
}
</script>

<style scoped>
.player{
    width: 10%;
    height: 4%;
    margin-bottom: 1.5rem;
    background: black;
}
</style>