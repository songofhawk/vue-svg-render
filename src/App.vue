<template>
    <div id="app">
        <img alt="Vue logo" src="./assets/logo.jpg">
        <SvgRender :svgData="svgData"/>
        <div>
            <button @click="changeR()">change</button>
        </div>
    </div>
</template>

<script>
    import SvgRender from './components/SvgRender.vue'

    export default {
        name: 'App',
        components: {
            SvgRender
        },
        data() {
            return {
                svgData: {
                    title: 'something happens',
                    graphs:[{
                        x:180,
                        y:90,
                        r:35,
                    }]
                }
            }
        },
        mounted() {

        },
        methods:{
            changeR(){
                let times = 0;
                setInterval(()=>{
                    this.svgData.graphs[0].r = 40*(Math.sin((times+=0.01))+1);
                },100)
            },
        }
    }
</script>

<style>
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
</style>
{
title: String,
likes: Number
}