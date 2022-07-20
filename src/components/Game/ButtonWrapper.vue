<script setup>
import Button from './Button.vue';

const props = defineProps({
    itemName: { type: String, required: true },
    isClickable: { type: Boolean, default: false },
    show: { type: Boolean, default: true },
    showRings: { type: Boolean, default: false }
})
</script>

<template>
    <div class="btn-wrapper rings">
        <template v-if="show">
            <div :class="{rings: showRings}">
                <Button :item-name="itemName" :is-clickable="isClickable" />
            </div>
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
.btn-wrapper .rings {
    position: relative;
    width: fit-content;
    height: fit-content;
    border-radius: 50%;
    box-shadow: 0 0 0 22px #ffffff0a;
}
.btn-wrapper .rings::before,
.btn-wrapper .rings::after {
    position: absolute;
    content: '';
    left: 50%;
    top: 50%;
    width: 185%;
    height: 185%;
    border-radius: 50%;
    transform: translate(-50%, -50%);
    background: #ffffff0a;
}
.btn-wrapper .rings::after {
    width: 230%;
    height: 230%;
}

.emptyCircle {
    width: 100px;
    height: 100px;
    border-radius: 50%;
    background-color: #00000022;
}


/* For large screens */

@media (min-width: 480px) {
    .btn-wrapper .rings {
        box-shadow: 0 0 0 50px #ffffff0a;
    }
    .btn-wrapper .rings::before {
        width: 200%;
        height: 200%;
    }
    .btn-wrapper .rings::after {
        width: 250%;
        height: 250%;
    }
    .emptyCircle {
        width: 150px;
        height: 150px;
        margin: 9px;
    }
}

@media (min-width: 760px) {
    .btn-wrapper .rings {
        box-shadow: 0 0 0 60px #ffffff0a;
    }
    .btn-wrapper .rings::before {
        width: 215%;
        height: 215%;
    }
    .btn-wrapper .rings::after {
        width: 270%;
        height: 270%;
    }
    .emptyCircle {
        width: 170px;
        height: 170px;
        margin: 17px;
    }
}
</style>