<script setup>
import Start from './Start.vue';
import Picked from './Picked.vue';
import { ref } from 'vue';

const props = defineProps({
    incrementScore: { type: Function, required: true }
})

const showStart = ref(true)
const showResult = ref(false)
const playerChoice = ref('')

const beats = {
    paper: ['rock'],
    rock: ['scissors'],
    scissors: ['paper']
}

const setPlayerChoice = (choice) => {
    playerChoice.value = choice
    setTimeout(() => {
        showResult.value = true
        showStart.value = false
    }, 300)
}

const evaluateChoice = (playerPick, housePick) => {
    if (playerPick === housePick) return 'TIE'
    let playerWin = beats[playerPick].includes(housePick)
    if (playerWin) {
        props.incrementScore()
        return 'WIN'
    }
    else return 'LOSE'
}

const playAgain = () => {
    playerChoice.value = ''
    showResult.value = false
    showStart.value = true
}

</script>

<template>
    <div class="game">
        <template v-if="showStart">
            <Start :set-choice="setPlayerChoice" />   
        </template>

        <template v-if="showResult && playerChoice">
            <Picked 
                :picked-item="playerChoice"
                :evaluate-choice="evaluateChoice"
                :play-again="playAgain"
            />
        </template>
    </div>
</template>

<style scoped>

</style>