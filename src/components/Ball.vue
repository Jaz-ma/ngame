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
            alert('game started')
        }
    }
}
</script>

<style scoped>
    #ball{
        background: black;
        margin-top: 5px;
        border: 1px solid gray;
        border-radius: 50%;
        height: 25px;
        width: 25px;
    }
</style>