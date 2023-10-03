<script setup>
    import comments from '../../comments.json'
    import TopComments from './TopComments.vue'
</script>

<template>
    <h1>Comments Data</h1>
    <TopComments :array="comments"/>
</template>

<style scoped>
    * {
        box-sizing: border-box;
        padding: 0;
        margin: 0;
    }
    h1 {
        text-align: center;
        margin-bottom: 1rem;
    }
</style>



