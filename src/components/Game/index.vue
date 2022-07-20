<script setup>
import Start from './Start.vue';
import Picked from './Picked.vue';
defineProps({
    msg: String
})
</script>

<template>
    <div class="game">
        <!-- <Start /> -->
        <Picked :picked-item="'paper'"/>

        <!-- TODO -->
        You Win - 
        You Lose - 

        Play Again
    </div>
</template>

<style scoped>

</style>