<template>
    <div id="app">
        <label>
            <input v-model="svgData.title"/>
        </label>
        <div>
        <svg xmlns="http://www.w3.org/2000/svg">
            <g v-for="graph in svgData.graphs" :key="graph.id">
                <circle :cx="graph.x" :cy="graph.y" :r="graph.r" stroke="black" stroke-width="2" fill="red" />
            </g>
        </svg>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'SvgRender',
        props: {
            svgData: {
                title:String,
                x:Number,
                y:Number,
                graphs:[{
                    x:Number,
                    y:Number,
                    r:Number,
                    id:Number
                }]
            },
        },
    }
</script>

<style>

</style>
