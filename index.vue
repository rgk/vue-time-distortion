<script setup>
import { ref, defineProps, onMounted, onUnmounted } from 'vue';

const props = defineProps({
  format: String,
  style: Number
});

const props = defineProps({
  locale: {
    type: String,
    default: 'en-US'
  },
  style: {
    type: Number,
    default: 0
});

let time = ref(new Date().toLocaleString(props.locale));
let hour = time.value.getHours();
let min = time.value.getMinutes();
let seconds = time.value.getSeconds();

let intervalId;

onMounted(() => {
  intervalId = setInterval(() => {
    time.value = new Date().toLocaleString(props.locale);
    hour = time.value.getHours();
    min = time.value.getMinutes();
    seconds = time.value.getSeconds();
  }, 1000);
});

onUnmounted(() => clearInterval(intervalId));
</script>

<template>
  <div>{{ time }}</div>
</template>

<style scoped>
</style>
