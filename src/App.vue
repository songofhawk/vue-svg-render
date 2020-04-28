<template>
    <div id="app">
        <img alt="Vue logo" src="./assets/logo.jpg">
        <SvgRender :svgMapping="svgMapping" :svgData="svgData"/>
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
                svgMapping: {
                    "graphs":"designAreas",
                    "graphType":"type",
                },
                svgData: {
                    title: 'something happens',
                    designAreas:[{
                        type:"image",
                        x:0,
                        y:0,
                        width:96,
                        height:96,
                        rotateX:30,
                        rotateY:30,
                        r:35,
                        color:"green",
                        href:"../image/logo.jpg",
                    },{
                        type:"text",
                        text:"wwww.tzding.com",
                        x:0,
                        y:0,
                        width:96,
                        height:96,
                        r:35,
                        color:"blue"
                    },]
                },
            }
        },
        mounted() {

        },
        methods:{
            changeR(){
                let times = 0;
                setInterval(()=>{
                    this.svgData.designAreas[0].r = 40*(Math.sin((times+=0.01))+1);
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