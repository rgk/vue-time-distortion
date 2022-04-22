<script setup>
import { ref, defineProps, onMounted, onUnmounted } from 'vue';

defineProps({
  format: String,
  style: Number
});

let time = ref(new Date().format(format));

let intervalId;

onMounted(() => {
  intervalId = setInterval(() => {
    time.value = new Date().format(format);
  }, 1000);
});

onUnmounted(() => clearInterval(intervalId));
</script>

<template>
  {{ time }}
  <slot></slot>
</template>
