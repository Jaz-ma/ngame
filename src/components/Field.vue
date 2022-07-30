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
            pos1: 0,
            pos2: 0,
            pos3: 0,
            pos4: 0,
        }
    },
    methods:{
        dragMouseDown(event,player_side){
            event = event || window.event;
            event.preventDefault;
            // get the mouse cursor position at startup:
            this.pos3 = event.clientX;
            console.log(this.pos3)
            document.onmouseup = this.closeDragElement
            document.addEventListener("mousemove", this.elementDrag)
        },

        closeDragElement(){
           document.removeEventListener("mousemove", this.elementDrag)
        },

        elementDrag(e){
            e = e || window.event;
            e.preventDefault();
            // calculate the new cursor position:
            this.pos1 = this.pos3 - e.clientX;
            this.pos3 = e.clientX;
            console.log(this.pos3)
            // set the element's new position:
            // elmnt.style.top = (elmnt.offsetTop - pos2) + "px";
            // elmnt.style.left = (elmnt.offsetLeft - pos1) + "px";console.log('hey')
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