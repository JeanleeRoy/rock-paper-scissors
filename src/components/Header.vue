<script setup>
defineProps({
  score: { type: Number, default: 0 }
})
</script>

<template>
    
    <header role="group">
      <div class="container">
        <img src="../assets/images/logo.svg" alt="Game logo">
        <div class="score">
          <p class="title">SCORE</p>
          <p class="value">{{ score }}</p>
        </div>
      </div>

    </header>

</template>

<style scoped>
header {
  width: 100%;
  padding: 1.2rem;
  margin: auto;
}
.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 12px;
  border-radius: 5px;
  border: 3px solid var(--header-outline);
}
header img {
  height: 50px;
  transform: translateY(3px) translateX(3px);
}
.score {
  display: flex;
  flex-wrap: wrap;
  width: 80px;
  height: 70px;
  margin: 0;
  background-color: hsl(0, 0%, 99%);
  border-radius: 5px;
  text-align: center;
}
.score .title {
  width: 100%;
  font-size: 10px;
  letter-spacing: 2px;
  font-weight: bolder;
  transform: translateY(10px);
  color: var(--score-text);
}
.score .value {
  width: 100%;
  color: var(--drk-text-color);
  font-size: 35px;
  font-weight: 700;
}

/* large */

@media (min-width: 480px) {
  header { max-width: 820px }
  header img { 
    height: 110px;
    margin-left: 3px;
  }
  .container {
    padding: 1.2rem 1.5rem;
    margin: 1rem auto;
    border-radius: 15px;
    border-width: 4px;
  }
  .score {
    height: 127px;
    width: 165px;
    border-radius: 10px;
  }
  .score .title {
    font-size: 18px;
    letter-spacing: 3px;
    font-weight: 600;
    transform: translateY(17px);
  }
  .score .value {
    font-size: 71px;
    line-height: 71px;
  }
}
</style>