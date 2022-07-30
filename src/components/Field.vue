<template>
    <div id="Field">
        <Player player_side="left" @playerTouched="dragMouseDown"/>
        <div id="mid">
            <Ball/>
            <Barrier/>
        </div>
        <Player player_side="right" @playerTouched="dragMouseDown"/>
    </div>
</template>

<script>
import Barrier from './Barrier.vue'
import Player from './Player.vue'
import Ball from './Ball.vue'
export default {
    name: 'Field',
    components:{
        Barrier,
        Player,
        Ball
    },
    data(){
        return{
            
        }
    },
    methods:{
        dragMouseDown(player_side){
            console.log(player_side);
        }
    }
}
</script>

<style scoped>
#Field{
    width: 50%;
    height: 43%;
    background: blue;
    display: flex;
    align-items: flex-end;
    justify-content: space-around;
}
#mid{
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
}
</style>