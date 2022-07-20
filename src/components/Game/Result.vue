<script setup>
import { ref, computed, onMounted } from 'vue'

const props = defineProps({
    result: { type: String, required: true },
    playAgain: { type: Function, required: true }
})

const textResult = computed(() => (
    props.result === 'TIE' ? 'TIE ROUND' : `YOU ${props.result}`
))

</script>

<template>
    <div class="game-result">
        <div class="result-content">
            <h3> {{textResult}} </h3>
            <button @click="playAgain()">PLAY AGAIN</button>
        </div>
    </div>
</template>

<style scoped>
.game-result,
.result-content {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
}
.game-result h3 {
    width: 100%;
    text-align: center;
    font-size: 3rem;
    margin-bottom: 1rem;
}
.game-result button {
    background-color: white;
    color: black;
    margin: auto;
    padding: 1rem 2.5rem;
    border-radius: .5rem;
    font-size: 1rem;
    letter-spacing: .15rem;
    box-shadow: 0 3px 3px #00000044;
    user-select: none;
}
.game-result button:active {
    box-shadow: 0 1px 1px #00000000;
    transform: scale(1.065);
}


/* For large screens */

@media (min-width: 760px) {
    .game-result {
        transform: translateY(2rem);
    }
    .game-result h3 {
        font-size: 3.5rem;
    }
}

</style>