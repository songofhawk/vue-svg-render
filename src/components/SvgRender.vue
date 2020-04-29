<template>
    <div id="svg-render">
        <div style="position: absolute">
            <svg xmlns="http://www.w3.org/2000/svg" style="left: 0; top: 0; width: 2000px; height: 1000px">
                <g>
                    <SvgItem v-for="graph in graphData[dataMapping.graphs]" :key="graph.id" :dataMapping="dataMapping.itemMapping" :graph="graph">
                    </SvgItem>
                </g>
            </svg>
        </div>
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
        methods: {
            getTransformOrigin(left, top, width, height) {
                const x = left + width / 2;
                const y = top + height / 2;
                return x + 'px ' + y + 'px';
            }
        }
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
