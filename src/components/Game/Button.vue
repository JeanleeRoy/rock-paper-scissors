<script setup>
const props = defineProps({
    primaryColor: { type: String, required: true },
    secondaryColor: { type: String, required: true },
    itemName: { type: String, required: true },
    itemStyle: { type: Object }
})

const imgSrc = `../../assets/images/icon-${props.itemName}.svg`
const btnImage = new URL(imgSrc, import.meta.url).href

</script>

<template>
    <div class="game-item" :style="itemStyle">
        <div class="game-item-content">
            <button class="game-btn">
                <img :src="btnImage" :alt="itemName">
            </button>
        </div>
    </div>
</template>

<style scoped>
.game-item {
    width: 120px;
    height: 120px;
    border-radius: 50%;
    transition: all ease .5s;
}
.game-item-content {
    position: relative;
    width: 121px;
    height: 121px;
    border-radius: 50%;
    background-color: #E3E3E3;
}
.game-item img {
    width: fit-content;
    height: fit-content;
    transform: translateX(-3px);
    z-index: 1;
}
.game-item .game-btn {
    position: absolute;
    display: flex;
    bottom: 0;
    width: 118px;
    height: 118px;
    align-items: center;
    justify-content: center;
    border-radius: 50%;
    outline: 17px solid v-bind(primaryColor);
    border-top: 6px solid #BEC0D5;
    z-index: 3;
}
.game-item .game-btn::after {
    position: absolute;
    content: "";
    left: -12px;
    top: 0;
    width: calc(100% + 24px);
    height: calc(100% + 14px);
    border-radius: 50%;
    border-bottom: 6px solid v-bind(secondaryColor);
    z-index: 1;
}
.game-item .game-btn:active {
    border-top: 7px solid #BEC0D5;
    height: 116px;
}
.game-item .game-btn:active img{
    transform: translateX(-3px) scaleY(.95);
}

@media (max-width: 400px) {
    .game-item {
        transform: scale(.8);
    }
    .game-item img {
        transform: scale(1.1);
    }
}
</style>