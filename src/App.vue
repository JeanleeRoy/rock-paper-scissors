<script setup>
import Header from "./components/Header.vue";
import Rules from "./components/Rules.vue";
import Game from "./components/Game/index.vue";
import { ref } from "vue";

const score = ref(0);

const incrementSocre = () => {
  score.value++
}

</script>

<template>
  <Header :score="score" />
  <Game :increment-score="incrementSocre" />
  <Rules />
</template>

<style>
</style>
