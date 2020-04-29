<template>
    <g style=""
       :style="{
        transform: 'rotateX('+ graph.rotateX+'deg) '+'rotateY('+ graph.rotateY+'deg)',
        transformOrigin:centerString
       }
    ">
        <image v-if="graph[dataMapping.graphType]==='image'" :href="graph.href" :x="virtualLeft" :y="virtualTop"
               :width="widthPct" :height="heightPct"
               :fill="graph.color || 'black'" :name="'graph-'+graph.id"/>

        <text v-if="graph[dataMapping.graphType]==='text'" :x="virtualLeft" :y="virtualTop"
              :fill="graph.color || 'black'" :textLength="boundaryWidthPct" :font-size="graph.height"
              :font-family = "graph.fontFamily.fontName"
              alignment-baseline="hanging" text-anchor="start" lengthAdjust="spacing"
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
                return (this.left* 100 / this.panel.width) + "%";
            },
            virtualTop() {
                return (this.top* 100 / this.panel.height) + "%";
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
            widthPct() {
                return this.virtualWidth ?
                    ((this.virtualWidth * 100 / this.panel.width).toFixed(2) + "%") :
                    null;
            },
            heightPct() {
                return this.virtualHeight ?
                    ((this.virtualHeight * 100 / this.panel.height).toFixed(2) + "%") :
                    null;
            },
            boundaryWidth(){
                return this.graph.width * this.graph.boundaryScaleX;
            },
            boundaryWidthPct(){
                return (this.boundaryWidth * 100 / this.panel.width).toFixed(2) + "%"
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
