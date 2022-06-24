<script setup>
import Button from './Button.vue';
const gameItems = [
    {
        itemName: "paper",
        itemStyle: {
            position: 'absolute',
            top: '0', left: '0'
        },
        primaryColor: "var(--paper-color)",
        secondaryColor: "var(--paper-color-2)"
    },
    {
        itemName: "scissors",
        itemStyle: {
            position: 'absolute',
            top: '0', right: '0'
        },
        primaryColor: "var(--scissors-color)",
        secondaryColor: "var(--scissors-color-2)"
    },
    {
        itemName: "rock",
        itemStyle: {
            position: 'absolute',
            top: 'auto', bottom: '0', left: '50%',
            transform: 'translateX(-50%)'
        },
        primaryColor: "var(--rock-color)",
        secondaryColor: "var(--rock-color-2)"
    }
]
</script>

<template>
    <div class="start-game">
        <div class="parent_polygon">
            <img class="main-triangle" src="../../assets/images/bg-triangle.svg" alt="Triangle">
            <!-- <div class="game-item">
                <div class="game-item-content">
                    <button class="ring">
                        <img src="../../assets/images/icon-paper.svg" alt="">
                    </button>
                </div>
            </div> -->
            <Button 
                v-for="item in gameItems"
                v-bind="item"
            />
        </div>
    </div>
</template>

<style scoped>
.start-game {
    display: flex;
    width: 100%;
    padding: 1rem;
    justify-content: center;
}
.parent_polygon {
    position: relative;
    padding: 40px;
    width: fit-content;
}
img.main-triangle {
    max-width: 100%;
}
</style>