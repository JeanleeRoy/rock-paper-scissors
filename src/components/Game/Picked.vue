<script setup>
import { ref, computed } from 'vue'
import Button from './Button.vue';

const props = defineProps({
    pickedItem: { type: String, required: false, default: "paper" },
})

const items = ['paper', 'scissors', 'rock']

const getHouseChoice = () => (
    items[Math.floor(Math.random()*items.length)]
)

</script>

<template>
    <div class="container">
        <div class="picked user-picked">
            <h2>YOU PICKED</h2>
            <div class="btn-wrapper">
                <Button 
                    :item-name="pickedItem"
                    :is-clickable="false"
                />
            </div>
        </div>
        <div class="picked house-picked">
            <h2>THE HOUSE PICKED</h2>
            <div class="btn-wrapper">
                <Button 
                    :item-name="getHouseChoice()"
                    :is-clickable="false"
                 />
            </div>
        </div>
    </div>
</template>

<style scoped>
.container {
    display: flex;
    width: 100%;
    max-width: 350px;
    margin: auto;
    padding: 0 1rem;
    justify-content: space-between;
}
.picked {
    display: inline-flex;
    flex-direction: column-reverse;
}
.picked h2 {
    text-align: center;
    font-size: 1rem;
    margin: 2rem 0 3rem;
}
.btn-wrapper {
    position: relative;
    display: flex;
    justify-content: center;
}


/* For large screens */

@media (min-width: 480px) {
    .container {
        max-width: 550px;
    }
}

@media (min-width: 760px) {
    .container {
        max-width: 700px;
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