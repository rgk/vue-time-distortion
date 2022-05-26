<script setup>
import { ref, defineProps, onMounted, onUnmounted } from 'vue';

const props = defineProps({
  format: String,
  style: Number
});

let time = ref(new Date().format(props.format));
let hour = time.value.getHours();
let min = time.value.getMinutes();
let seconds = time.value.getSeconds();

let intervalId;

onMounted(() => {
  intervalId = setInterval(() => {
    time.value = new Date().format(format);
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
