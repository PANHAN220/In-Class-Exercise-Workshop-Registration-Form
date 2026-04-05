<script setup>
defineProps(['label', 'class'])
</script>

<template>
  <button :class="['px-4 py-2 m-1.5 font-bold rounded-4xl', $props.class]">
    {{ label }}
  </button>
</template>