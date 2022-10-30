<template>
  <div class="typing-container">
    <div></div>

    <div></div>
    <div></div>
  </div>
</template>

<script setup lang="ts"></script>

<style scoped lang="scss">
.typing-container {
  display: flex;
  justify-content: center;
  gap: 10px;
  align-items: center;

  div {
    border-radius: 100%;
    width: 25px;
    height: 25px;
    opacity: 0.8;
    background-color: lightseagreen;
    animation: bounce ease-out infinite 1s;
    &:nth-child(2) {
      animation-delay: 250ms;
      opacity: 0.6;
    }
    &:nth-child(3) {
      opacity: 0.4;
      animation-delay: 500ms;
    }
  }
}
@keyframes bounce {
  0% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-20px);
  }
  100% {
    transform: translateY(0px);
  }
}
</style>
