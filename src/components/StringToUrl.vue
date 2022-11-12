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

const convertedString = ref("");
const searchInput = ref("");

function convertInput(): void {
  convertedString.value = stringToLink(searchInput.value);
}

function stringToLink(text: string): string {
  const shortURL: RegExp = /^([a-zA-Z0-9]+(\.[a-zA-Z0-9]+)+.*)$/;
  const normalUrl: RegExp =
    /^(https?:\/\/)?([\da-z.-]+)\.([a-z.]{2,6})([/\w .-]*)*\/?$/;
  const searchHTMlTag: RegExp = /(<|>)/;
  let editedString: string = "invalid characters please remove < and or >";
  const searchForHTMlTags: string = text.split(" ").join("");
  if (!searchForHTMlTags.match(searchHTMlTag)) {
    const splitStringArray: string[] = text.split(" ");
    const convertedArray: string[] = splitStringArray.map((url) => {
      if (url.match(shortURL)) {
        return `<a href="https://${url}" target="_blank" >${url}</a>`;
      } else if (url.match(normalUrl)) {
        const urlText = url.replace("https://", "").replace("http://", "");
        return `<a href="${url}" target="_blank" >${urlText}</a>`;
      }
      return url;
    });

    editedString = convertedArray.join(" ");
  }

  return editedString;
}
</script>

<style scoped lang="scss"></style>
