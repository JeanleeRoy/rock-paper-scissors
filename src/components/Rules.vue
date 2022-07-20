<script setup>
import { ref } from 'vue';

const openRules = ref(false)

const closeModal = () => {
    openRules.value = false
}

</script>

<template>
    <div class="r-container">
        <button class="open" @click="openRules = true">RULES</button>
    </div>
    
    <Teleport to="body">
        <div v-show="openRules">
            <div class="modal">
                <div class="modal-bg" @click="closeModal()"></div>
                <div class="modal-content">
                    <div class="modal-container">
                        <h3>RULES</h3>
                        <img class="rules-img" src="../assets/images/image-rules.svg" alt="game rules">
                        <button class="close" @click="closeModal()">
                            <img src="../assets/images/icon-close.svg" alt="">
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </Teleport>
</template>

<style scoped>
.r-container {
    position: fixed;
    bottom: 1rem;
    right: 1rem;
    width: 90%;
    max-width: 1100px;
    z-index: 0;
}
button.open {
    float: right;
    padding: .5rem 1.5rem;
    border: 1px solid var(--content-color);
    border-radius: .5rem;
    user-select: none;
}
button.open:active {
    transform: scale(1.07);
}
.modal {
    display: flex;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    justify-content: center;
    align-items: center;
    z-index: 10;
}
.modal-bg {
    position: absolute;
    width: 100%;
    height: 100%;
    background-color: #00000090;
    z-index: 10;
}
.modal-content {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 100%;
    background-color: var(--content-color);
    z-index: 12;
}
.modal-container {
    display: grid;
    row-gap: 5rem;
    grid-template-areas: 
    "title"
    "rules"
    "close";
}
.modal-content h3 {
    color: var(--main-color);
    text-align: center;
    font-size: 2rem;
    grid-area: title;
}
.modal-content .rules-img {
    grid-area: rules;
}
.modal-content .close {
    margin: auto;
    grid-area: close;
}


/* For large screens */

@media (min-width: 480px) {
    .modal-content {
        width: fit-content;
        height: fit-content;
        padding: 2rem 2.5rem;
        border-radius: .6rem;
    }
}

@media (min-width: 760px) {
    .r-container {
        right: 50%;
        bottom: 2rem;
        transform: translateX(50%);
    }
    button.open {
        font-size: 1rem;
        letter-spacing: .2rem;
        padding: .6rem 1.7rem .6rem 1.9rem;
    }
    .modal-container {
        display: grid;
        row-gap: 3rem;
        grid-template-columns: 10fr 2fr;
        grid-template-areas: 
        "title close"
        "rules rules";
    }
    .modal-content h3 {
        text-align: left;
        font-size: 2.2rem;
    }
    .modal-content .rules-img {
        margin: .5rem 1.5rem;
    }
    .modal-content .close {
        margin: 0;
    }
    .modal-content .close img {
        float: right;
    }
}
</style>