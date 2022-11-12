<template>
  <div class="home-container">
    <!-- <SpinnerComponent />
    <Spinner2Component />
    <Spinner3Component />
    <TypingSpinnerVue /> -->
    <SearchContent />
    <StringToUrl />
  </div>
</template>
<script setup lang="ts">
import SpinnerComponent from "@/components/spinners/SpinnerComponent.vue";
import Spinner2Component from "@/components/spinners/Spinner2Component.vue";
import Spinner3Component from "@/components/spinners/Spinner3Component.vue";
import TypingSpinnerVue from "@/components/spinners/TypingSpinner.vue";
import SearchContent from "@/components/searchContent/searchContent.vue";
import StringToUrl from "@/components/StringToUrl.vue";
</script>

<style>
.home-container {
  width: 100%;
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  gap: 40px;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}
</style>
