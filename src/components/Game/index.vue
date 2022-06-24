<script setup>
import Start from './Start.vue';
defineProps({
    msg: String
})
</script>

<template>
    <div class="game">
        <Start />
        <!-- TODO -->
        You Picked - 
        The House Picked - 

        You Win - 
        You Lose - 

        Play Again
    </div>
</template>

<style scoped>

</style>