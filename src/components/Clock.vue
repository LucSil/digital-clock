<template>
  <div class="clock">
    <span class="hr">{{ hr }}</span> : <span class="min">{{ min }}</span> :
    <span class="sec">{{ sec }}</span> <span class="ampm">{{ ampm }}</span>
  </div>
</template>

<script>
import { ref } from "@vue/reactivity";
export default {
  setup() {
    let d = new Date();

    let hr = setInterval(() => {
      d.getHours();
    }, 1000);
    let min = d.getMinutes() < 10 ? `0${d.getMinutes()}` : d.getMinutes();
    let sec = setInterval(() => {
      d.getSeconds() < 10 ? `0${d.getSeconds()}` : d.getSeconds();
    }, 1000);
    let ampm = d.getHours() >= 12 ? "PM" : "AM";

    return { hr, min, sec, ampm };
  },
};
</script>

<style></style>
