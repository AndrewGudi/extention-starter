<template lang="pug">
.options
  h1 Options Page
  p You can use scss
  button(@click="onClick") Here is a counter: {{ counter }}
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";
import browser from "webextension-polyfill";

onMounted(() => {
  // Can access web-extension api through Vue files
  // Sends a message to the background script every time the popup is opened
  browser.runtime.sendMessage({ from: "OptionsScreen.vue" });
});

const counter = ref(0);

const onClick = () => {
  counter.value++;
};
</script>

<style lang="scss">
div {
  text-align: center;
  p {
    color: red;
  }
}
</style>
