<template>
  <div>String To URL</div>
  <textarea
    @keyup="convertInput"
    type="text"
    v-model="searchInput"
    placeholder="string to url"
  />
  BIO:
  <span v-html="convertedString"></span>
</template>

<script setup lang="ts">
import { ref } from "vue";

const shortURL = /^([a-zA-Z0-9]+(\.[a-zA-Z0-9]+)+.*)$/;
const normalUrl = /^(https?:\/\/)?([\da-z.-]+)\.([a-z.]{2,6})([/\w .-]*)*\/?$/;
const searchHTMlTag = /(<|>)/;
const convertedString = ref("");
const searchInput = ref("");

function convertInput(): void {
  const searchForHTMlTags = searchInput.value.split(" ").join("");
  if (!searchForHTMlTags.match(searchHTMlTag)) {
    const splitStringArray = searchInput.value.split(" ");

    const convertedArray = splitStringArray.map((url) => {
      if (url.match(shortURL)) {
        return `<a href="https://${url}" target="_blank" >${url}</a>`;
      } else if (url.match(normalUrl)) {
        return `<a href="${url}" target="_blank" >${url}</a>`;
      }
      return url;
    });

    convertedString.value = convertedArray.join(" ");
  } else {
    convertedString.value = "invalid characters please remove < and >";
  }
}
</script>

<style scoped lang="scss"></style>
