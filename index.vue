<script setup>
import { ref, defineProps, onMounted, onUnmounted } from 'vue';

defineProps({
  format: String,
  style: Number
});

let time = ref(Date.now());

let intervalId;

onMounted(() => {
  intervalId = setInterval(() => {
    time.value = Date.now();
  }, 1000);
});

onUnmounted(() => clearInterval(intervalId));
</script>

<template>
  {{ time }}
  <slot></slot>
</template>
