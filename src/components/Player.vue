<template>
    <div ref="player" class="player" @mousedown="dragMouseDown">
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
            let player = this.$refs.player
            console.log(player)
            // set the element's new position:
            // elmnt.style.top = (elmnt.offsetTop - pos2) + "px";
            // elmnt.style.left = (elmnt.offsetLeft - pos1) + "px";console.log('hey')
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