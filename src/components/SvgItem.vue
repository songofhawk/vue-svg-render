<template>
    <g style=""
       :style="{
        transform: 'rotateX('+ graph.rotateX+'deg) '+'rotateY('+ graph.rotateY+'deg)',
        transformOrigin:centerString
       }
    ">
        <image v-if="graph[dataMapping.graphType]==='image'" :href="graph.href" :x="graph.x" :y="graph.y"
               :width="graph.width" :height="graph.height"
               :fill="graph.color || 'black'"/>

        <text v-if="graph[dataMapping.graphType]==='text'" :x="graph.x" :y="graph.y"
              :fill="graph.color || 'black'"
              alignment-baseline="hanging" text-anchor="start"
        >{{graph.text}}
        </text>
    </g>
</template>

<script>
    export default {
        name: 'SvgItem',
        props: {
            dataMapping: {
                graphType: String,
            },
            graph: Object,
            // svgData: {
            //     title:String,
            //     x:Number,
            //     y:Number,
            //     graphs:[{
            //         x:Number,
            //         y:Number,
            //         r:Number,
            //         id:Number
            //     }]
            // },
        },
        // data: function () {
        //     return {
        //         style:{
        //             graphItem:{
        //                 transformOrigin:this.getTransformOrigin()
        //             }
        //         }
        //     };
        // },
        beforeMount() {
            console.log(".....");
        },
        computed: {
            centerX() {
                return this.graph.x + this.graph.width / 2;
            },
            centerY() {
                return this.graph.y + this.graph.height / 2;
            },
            centerString() {
                return this.centerX + 'px ' + this.centerY + 'px';
            }
        }
        ,
        methods: {}
        ,
        beforeCreate() {
            // this.svgData = {
            //     title:String,
            //     cat:String,
            //     x:Number,
            //     y:Number,
            //     graphs:[{
            //         x:Number,
            //         y:Number,
            //         r:Number,
            //         id:Number
            //     }]
            // };
            // console.log(this.svgData);
        }
        ,
    }
</script>

<style>

</style>
