<template>
    <div id="svg-render" style="position: absolute;margin: 0;padding: 0;border: none;font-size: 1em;width: 98%">
        <img :src="graphData[dataMapping.bgImage]" style="left: 0; top: 0; display:block ;width: 100%" alt="正在加载背景图..."/>
        <svg xmlns="http://www.w3.org/2000/svg"
             style="position:absolute; left: 0; top: 0; width: 100%; height: 100%;">
            <SvgItem v-for="graph in graphData[dataMapping.graphs]" :key="graph.id"
                     :dataMapping="dataMapping.itemMapping" :graph="graph" :panel="panelDataForGraph">
            </SvgItem>
        </svg>
    </div>
</template>

<script>
    import SvgItem from "./SvgItem";

    export default {
        name: 'SvgRender',
        components: {SvgItem},
        props: {
            dataMapping: {
                graphs: String,
                bkImage: String,
                itemMapping: Object,
            },
            graphData: Object,
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
        computed:{
            panelDataForGraph(){
              return {
                  width:this.graphData.width,
                  height:this.graphData.height
              }
            },
        },
        methods: {
            getTransformOrigin(left, top, width, height) {
                const x = left + width / 2;
                const y = top + height / 2;
                return x + 'px ' + y + 'px';
            }
        }
        ,
        beforeCreate() {
            console.log("SvgRender.vue beforeCreate");
        }
        ,
        mounted() {
            console.log("SvgRender.vue mounted");
        }
        ,
    }
</script>

<style>

</style>
