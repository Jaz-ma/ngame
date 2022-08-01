<template>
    <div ref="ball" id="ball"></div>   
</template>

<script>
import { watch } from '@vue/runtime-core'

export default {
    name: 'Ball',
    props:{
        Game_started:{
            type: Boolean,
        }
    },
    watch:{
        Game_started()
        {
            this.animateBall()
        }
    },
    methods:{
        animateBall()
        {
            let ball = document.getElementById('ball')
            let ball_pos = ball.getBoundingClientRect()
            let ball_x =ball_pos.left
            let ball_y =ball_pos.top

            ball.style.left = ball_x  + 'px'
            console.log(ball_x)
        }
    }
}
</script>

<style scoped>
    #ball{
        position: relative;
        background: black;
        margin-top: 5px;
        border: 1px solid gray;
        border-radius: 50%;
        height: 25px;
        width: 25px;
    }
</style>