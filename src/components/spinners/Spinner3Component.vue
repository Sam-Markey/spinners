<template>
  <div class="spinner-container">
    <div></div>
    <div></div>
    <div></div>
  </div>
</template>

<script setup lang="ts"></script>

<style scoped lang="scss">
.spinner-container {
  position: relative;
  width: 100px;
  height: 100px;

  div {
    perspective: 300px;
    position: absolute;
    width: 100%;
    height: 100%;
    border: solid 5px lightskyblue;
    border-radius: 50%;
    animation: 2s expandFadeOut infinite ease-in-out;

    &:nth-child(2) {
      animation-delay: 300ms;
      border-color: lightgreen;
    }
    &:nth-child(3) {
      animation-delay: 600ms;
      border-color: lightseagreen;
    }
  }
}

@keyframes expandFadeOut {
  0% {
    transform: scale(0);
    opacity: 1;
  }
  50% {
    transform: scale(1) rotate3d(0.5, 1, 0, 360deg);
  }
  100% {
    transform: scale(0);
    opacity: 1;
  }
}
</style>
