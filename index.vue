<script setup>
import { ref, defineProps, onMounted, onUnmounted } from 'vue';

import { SVG } from '@svgdotjs/svg.js';

const props = defineProps({
  locale: {
    type: String,
    default: 'en-US'
  },
  style: {
    type: Number,
    default: 0
  }
});

let draw = SVG().addTo('body').size(250, 250);
let rect = draw.rect(100, 100).attr({ fill: '#cccccc' });

let time = ref(new Date().toLocaleString(props.locale));
let hours = ref(time.value.getHours());
let minutes = ref(time.value.getMinutes());
let seconds = ref(time.value.getSeconds());

let intervalId;

onMounted(() => {
  intervalId = setInterval(() => {
    time.value = new Date().toLocaleString(props.locale);
    hours.value = time.value.getHours();
    minutes.value = time.value.getMinutes();
    seconds.value = time.value.getSeconds();
  }, 1000);
});

onUnmounted(() => clearInterval(intervalId));
</script>

<template>
  <div>{{ time }}</div>
</template>

<style scoped>
</style>
