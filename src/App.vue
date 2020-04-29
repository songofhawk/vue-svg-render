<template>
    <div id="app" style="width: 100%;position: relative">
        <img alt="Vue logo" src="./assets/logo.jpg">
        <SvgRender :dataMapping="dataMapping" :graphData="graphData.viDesign" style="width: 100%"/>
        <div>
            <button @click="changeR()">change</button>
        </div>
    </div>
</template>

<script>
    import SvgRender from './components/SvgRender.vue'
    import viDesign from './assets/data/vi_design.json'
    import state from './assets/data/state.json'

    const cmContent = state.payload.cmCustomInfo;
    const cmCustomInfos = state.payload.cmCustom.cmCustomInfos;
    const cmInfos = {};
    for (let cmcInfo of cmCustomInfos) {
        let key = cmcInfo.infoType;
        cmInfos[key] = {
            content: cmContent[key],
            aspectRatio: cmcInfo.aspectRatio,
        }
    }
    viDesign.payload.detailImages[0].pgDesignAreaImageLabels.forEach((designArea)=>{
        const infoType = designArea.infoType;
        const cmInfo = cmInfos[infoType];
        if (!cmInfo){
            return;
        }
        let content = cmInfo.content;
        designArea.aspectRatio = cmInfo.aspectRatio;
        if (infoType==="LOGO" || infoType==="PERSONAL_QRCODE" || infoType==="PHOTO"){
            designArea.graphType = 'image';
            designArea.href = content ? content : null;
        }else{
            designArea.graphType = 'text';
            designArea.text = content ? content : null;
        }
    });

    export default {
        name: 'App',
        components: {
            SvgRender
        },
        data() {
            return {
                dataMapping: {
                    "graphs": "pgDesignAreaImageLabels",
                    "bgImage": "file",
                    itemMapping: {
                        "graphType": "graphType",
                    }
                },
                graphData: {
                    title: 'something happens',
                    viDesign:viDesign.payload.detailImages[0],
                    designAreas: [{
                        type: "image",
                        x: 0,
                        y: 0,
                        width: 96,
                        height: 96,
                        rotateX: 30,
                        rotateY: 30,
                        r: 35,
                        color: "green",
                        href: "../image/logo.jpg",
                    }, {
                        type: "text",
                        text: "wwww.tzding.com",
                        x: 0,
                        y: 0,
                        width: 96,
                        height: 96,
                        r: 35,
                        color: "blue"
                    },]
                },
            }
        },
        mounted() {
            console.log("app.vue mounted");
        },
        methods: {
            changeR() {
                /* eslint-disable no-debugger */
                let times = 0;
                setInterval(() => {
                    this.svgData.designAreas[0].r = 40 * (Math.sin((times += 0.01)) + 1);
                }, 100)
                /* eslint-enable no-debugger */
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