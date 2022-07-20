<script setup>
import { ref, computed, onMounted } from 'vue'
import ButtonWrapper from './ButtonWrapper.vue';
import Result from './Result.vue';

const props = defineProps({
    pickedItem: { type: String, required: false, default: "paper" },
    evaluateChoice: { type: Function, required: true },
    playAgain: { type: Function, required: true }
})

const items = ['paper', 'scissors', 'rock']
const houseChoice = ref('')
const gameResut = ref('') // WIN | LOSE | TIE

const setHouseChoice = () => {
    houseChoice.value = items[Math.floor(Math.random()*items.length)]
}

const setGameResult = () => {
    gameResut.value = props.evaluateChoice(props.pickedItem, houseChoice.value)
}

onMounted(() => {
    setTimeout(() => {
        setHouseChoice()
        setTimeout(() => setGameResult(), 400)
    }, 400)
})

</script>

<template>
    <div class="container" :class="{span: gameResut}">
        <div class="picked player-picked">
            <h2>YOU PICKED</h2>
            <ButtonWrapper 
                :item-name="pickedItem"
                :show-rings="gameResut === 'WIN'"
            />
        </div>
        
        <div class="picked house-picked">
            <h2>THE HOUSE PICKED</h2>
            <ButtonWrapper 
                :item-name="houseChoice"
                :show="houseChoice !== ''"
                :show-rings="gameResut === 'LOSE'"
            />
        </div>

        <template v-if="gameResut">
            <Result class="result" 
                :result="gameResut" 
                :play-again="playAgain"
            />
        </template>
    </div>
</template>

<style scoped>
.container {
    display: grid;
    width: 100%;
    max-width: 450px;
    margin: auto;
    padding: 0 1rem;
    padding-top: 3rem;
    grid-template-columns: 1fr 1fr;
    grid-template-areas: 
        "player house"
        "result result";
}
.picked {
    display: inline-flex;
    flex-direction: column-reverse;
    /* justify-content: start; */
}
.house-picked {
    grid-area: house;
}
.player-picked {
    grid-area: player;
}
.picked h2 {
    text-align: center;
    font-size: 1rem;
    margin: 2rem 0 3rem;
}
.result {
    grid-area: result;
}


/* For large screens */

@media (min-width: 480px) {
    .container {
        padding-top: 2rem;
        max-width: 600px;
    }
}

@media (min-width: 760px) {
    .container {
        max-width: 700px;
        padding-top: 1rem;
    }
    .container.span {
        max-width: 800px;
        grid-template-columns: 1fr 1fr 1fr;
        grid-template-areas: "player result house";
    }
    .picked {
        flex-direction: column;
        /* transform: scale(1.2); */
    }
    .picked h2 {
        font-size: 1.5rem;
        letter-spacing: .15rem;
    }
}
</style>