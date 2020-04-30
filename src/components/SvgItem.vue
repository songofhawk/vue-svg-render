<template>
    <g style=""
       :style="{
        transform: 'rotateX('+ graph.rotateX+'deg) '+'rotateY('+ graph.rotateY+'deg)',
        transformOrigin:centerString
       }
    ">
        <image v-if="graph[dataMapping.graphType]==='image'" :href="graph.href" :x="virtualLeft" :y="virtualTop"
               :width="virtualWidth" :height="virtualHeight"
               :fill="graph.color || 'black'" :name="'graph-'+graph.id"/>

        <text v-if="graph[dataMapping.graphType]==='text'" :x="virtualLeft" :y="virtualTop"
              :fill="graph.color || 'black'" :font-size="graph.height"
              :font-family = "graph.fontFamily.fontName"
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
            panel: Object,
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
            left() {
                return this.graph.x - this.graph.width / 2;
            },
            top() {
                return this.graph.y - this.graph.height / 2;
            },
            virtualLeft() {
                if (this.graph.align==="left"){
                    return this.left;
                }else if (this.graph.align==="right"){
                    return this.graph.x + this.graph.width / 2 - this.virtualWidth;
                }else {
                    return this.graph.x - this.virtualWidth/2;
                }
            },
            virtualTop() {
                if (this.graph.verticalAlign==="top"){
                    return this.top;
                }else if (this.graph.align==="bottom"){
                    return this.graph.y + this.graph.height / 2 - this.virtualHeight;
                }else {
                    return this.graph.y - this.virtualHeight/2;
                }
            },
            centerString() {
                return this.graph.x + 'px ' + this.graph.y + 'px';
            },
            virtualHeight() {
                const area = this.graph.width * this.graph.height;
                return this.graph.aspectRatio ? Math.sqrt(area / this.graph.aspectRatio): null;
            },
            virtualWidth(){
                return this.graph.aspectRatio ? this.virtualHeight * this.graph.aspectRatio : null;
            },
            boundaryWidth(){
                return this.graph.width * this.graph.boundaryScaleX;
            },

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
