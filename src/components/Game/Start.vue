<script setup>
import Button from './Button.vue';

</script>

<template>
    <div class="start-game">
        <div class="parent_polygon">
            <img class="main-triangle" src="../../assets/images/bg-triangle.svg" alt="Triangle">

            <Button 
                :item-name="'paper'"
                :primary-color="'var(--paper-color)'"
                :secondary-color="'var(--paper-color-2)'"
                class="g-btn g-btn-paper"
            />
            <Button 
                :item-name="'scissors'"
                :primary-color="'var(--scissors-color)'"
                :secondary-color="'var(--scissors-color-2)'"
                class="g-btn g-btn-scissors"
            />
            <Button 
                :item-name="'rock'"
                :primary-color="'var(--rock-color)'"
                :secondary-color="'var(--rock-color-2)'"
                class="g-btn g-btn-rock"
            />

        </div>
    </div>
</template>

<style scoped>
.start-game {
    display: flex;
    width: 100%;
    padding: 1rem;
    margin-top: 50px;
    justify-content: center;
}
.parent_polygon {
    position: relative;
    padding: 40px;
    width: 300px;
    max-width: 100%;
}
img.main-triangle {
    max-width: 100%;
}
.g-btn {
    position: absolute;
    top: auto;
}
.g-btn-paper {
    top: 0;
    left: 0;
}
.g-btn-scissors {
    top: 0;
    right: 0;
}
.g-btn-rock {
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);
}

/* For medium screens */

@media (min-width: 480px) {
    .parent_polygon {
        padding-top: 50px;
        width: fit-content;
    }
    .g-btn-paper {
        top: -20px;
        left: -20px;
    }
    .g-btn-scissors {
        top: -20px;
        right: -20px;
    }
}

/* For large screens */

@media (min-width: 760px) {
    .parent_polygon {
        margin-top: 20px;
    }
    .g-btn-paper {
        top: -50px;
        left: -60px;
    }
    .g-btn-scissors {
        top: -50px;
        right: -60px;
    }
    .g-btn-rock {
        bottom: -50px;
    }
}
</style>