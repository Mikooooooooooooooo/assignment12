<template>
    <div class="app">
        <div class="title">
            {{ title }}
        </div>
        <div v-if="show" class="text">
            {{ text_1 }}
        </div>
        <input type="text" class="inputter" v-else v-model="text_1" >
    </div>
</template>

<script>
    export default{
        data() {
            return{
                text_1: this.text
            }
        } , 
        props: ['title' , 'text' , 'show'] 
    }
</script>

<style>
    .app{
        display: flex ; 
        padding: 1vh 0 ; 
    }

    .title{
        width: 10% ; 
        color: black ; 
    }

    .inputter{
        display: block ;
        width: 100% ;
        margin-bottom: 0.5vh ; 
        border: none;
        outline: none;
        border-bottom: 1px solid #ccc; 
        background: #3d3d3d ; 
    }
</style>