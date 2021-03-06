<script setup>
import { computed } from '@vue/reactivity';

const props = defineProps({
    itemName: { type: String, required: true },
    primaryColor: { type: String },
    secondaryColor: { type: String },
    isClickable: {type: Boolean, default: true}
})

const firstColor = computed(() => (
    props.primaryColor || `var(--${props.itemName}-color)`
))

const secondColor = computed(() => (
    props.secondaryColor || `var(--${props.itemName}-color-2)`
))

const btnImage = computed(() => {
    return new URL(`../../assets/images/icon-${props.itemName}.svg`, import.meta.url).href
})

</script>

<template>
    <div class="game-item">
        <button class="game-btn" :class="{clickable: isClickable, defaultPointer: !isClickable}">
            <img :src="btnImage" :alt="itemName">
        </button>
    </div>
</template>

<style scoped>
.game-item {
    width: fit-content;
    height: fit-content;
    padding-bottom: 5px;
}
.game-btn {
    display: flex;
    width: 90px;
    height: 90px;
    border-radius: 50%;
    justify-content: center;
    align-items: center;
    background-color: #E3E3E3;
    border: 14px solid v-bind(firstColor);
    box-shadow: 0 5px 0 v-bind(secondColor),
                0 5px 5px #00000055,
                inset 0 4px 0 #BEC0D5;
}

.game-btn img {
    width: 43px;
    height: 43px;
    object-fit: contain;
    transform: translateY(2px);
}

.game-btn.clickable:active {
    transform: translateY(2px);
    box-shadow: 0 3px 0 v-bind(secondColor),
                0 5px 5px #0000002d,
                inset 0 4px 0 #BEC0D5;
}

.game-btn.defaultPointer {
    cursor: default;
}


/* For large screens */

@media (min-width: 480px) {
    .game-btn {
        width: 130px;
        height: 130px;
        border-width: 19px;
        box-shadow: 0 8px 0 v-bind(secondColor),
                0 8px 8px #00000055,
                inset 0 7px 0 #BEC0D5;
    }
    .game-btn img {
        width: 68px;
        height: 68px;
        transform: translate(-1px, 2px);
    }
}

@media (min-width: 760px) {
    .game-btn {
        width: 160px;
        height: 160px;
        border-width: 25px;
        box-shadow: 0 9px 0 v-bind(secondColor),
                0 9px 10px #00000055,
                inset 0 8px 0 #BEC0D5;
    }
    .game-btn img {
        width: 84px;
        height: 84px;
        transform: translate(-1px, 2px);
    }
    .game-btn.clickable:active {
        transform: translateY(5px);
        box-shadow: 0 4px 0 v-bind(secondColor),
                    0 6px 6px #0000002d,
                    inset 0 4px 0 #BEC0D5;
    }
}
</style>