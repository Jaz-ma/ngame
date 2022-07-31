<template>
    <div id="Field">
        <Player player_side="left" style="left: 100px" />
        <div id="mid">
            <Ball/>
            <Barrier/>
        </div>
        <Player player_side="right" style="right: 100px;" />
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
            pos1: 0,
            pos2: 0,
            pos3: 0,
            pos4: 0,
        }
    },
    methods:{
        
    }
}
</script>

<style scoped>
#Field{
    position: relative;
    width: 50%;
    height: 43%;
    background: blue;
    display: flex;
    align-items: flex-end;
    justify-content:center;
}
#mid{
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
}
</style>