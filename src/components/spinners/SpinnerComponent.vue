<template>
  <div>
    Spinner 1
    <div class="spinner-container"></div>
  </div>
</template>

<script setup lang="ts"></script>

<style scoped lang="scss">
.spinner-container {
  width: 100px;
  height: 100px;
  border: solid 8px darkgray;
  border-radius: 100%;
  border-bottom-color: rgb(179, 107, 182);
  animation: rotate360 infinite 1s linear;
}

@keyframes rotate360 {
  100% {
    transform: rotate(360deg);
  }
}
</style>
