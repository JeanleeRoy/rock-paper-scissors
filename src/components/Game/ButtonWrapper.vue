<script setup>
import Button from './Button.vue';

const props = defineProps({
    itemName: { type: String, required: true },
    isClickable: { type: Boolean, default: false },
    show: { type: Boolean, default: true }
})
</script>

<template>
    <div class="btn-wrapper">
        <template v-if="show">
            <Button :item-name="itemName" :is-clickable="isClickable" />
        </template>
        <div v-else class="emptyCircle">
        </div>
    </div>
</template>

<style scoped>
.btn-wrapper {
    position: relative;
    display: flex;
    justify-content: center;
}
.emptyCircle {
    width: 100px;
    height: 100px;
    border-radius: 50%;
    background-color: #00000022;
}


/* For large screens */

@media (min-width: 480px) {
    .emptyCircle {
        width: 150px;
        height: 150px;
        margin: 9px;
    }
}

@media (min-width: 760px) {
    .emptyCircle {
        width: 170px;
        height: 170px;
        margin: 17px;
    }
}
</style>