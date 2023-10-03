<script setup>
    import ShowComments from './ShowComments.vue';
   
    defineProps(['array']) ;
</script>

<template>
    <div class="container">
        <div v-for="(item) in array" :key="item._id">
            <ShowComments :comment="item"/>
        </div>
    </div>
</template>

<style scoped>
    .container {
        max-width: 500px;
        margin: 0 auto;
    }
</style>