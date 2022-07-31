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
      dragMouseDown(event){
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


            // this function needs improving, player block can phase outside the borders a bit 


        elementDrag(e){
            e = e || window.event;
            e.preventDefault();
            // calculate the new cursor position:
            let player = this.$refs.player
            let rect = player.getBoundingClientRect()
            let Barrier = document.getElementById('barrier').getBoundingClientRect()
            let Field = document.getElementById('Field').getBoundingClientRect()
            this.pos1 = this.pos3 - e.clientX;
            this.pos3 = e.clientX;

            // set the element's new position:
            if(this.player_side =="right")
            {
                if (rect.left > Barrier.right && Math.abs(this.pos1) < 30 && rect.right < Field.right )
                {
                    player.style.left = (player.offsetLeft - this.pos1) + "px"
                }
                else
                {
                    if(rect.right > Field.right)
                player.style.left = (player.offsetLeft - 0.8) + "px"

                    if(rect.left < Barrier.right)
                player.style.left = (player.offsetLeft + 0.8) + "px"
            }

            }
            else if(this.player_side =="left")
            {
                console.log(this.player_side)
                if (rect.right < Barrier.left && Math.abs(this.pos1) < 30 && rect.left > Field.left )
                {
                     player.style.left = (player.offsetLeft - this.pos1) + "px"
                }
                else
                {
                    if(rect.left > Field.left)
                        player.style.left = (player.offsetLeft - 0.8) + "px"

                    if(rect.right < Barrier.left)
                        player.style.left = (player.offsetLeft + 0.8) + "px"
            }
            } 


            // console.log("player: " ,rect.left)
            // console.log("Field: " ,Field.right)
            // console.log("barrier: " ,Barrier.right)
        }
    },
}
</script>

<style scoped>
.player{
    position: absolute;
    width: 10%;
    height: 4%;
    margin-bottom: 1.5rem;
    background: black;
}
</style>