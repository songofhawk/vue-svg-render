<template>
    <div id="app">
        <img alt="Vue logo" src="./assets/logo.jpg">
        <SvgRender :title="svgData.title"/>
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
                    title: 'something happens'
                }
            }
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