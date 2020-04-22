<template>
    <div id="app">
        <label> title:
            <input v-model="title"/>
        </label>
    </div>
</template>

<script>
    export default {
        name: 'SvgRender',
        props: {
            title:String,
        },
    }
</script>

<style>

</style>
