<script setup>
defineProps(['label', 'class'])
</script>

<template>
  <button :class="['px-4 py-2 rounded', $props.class]">
    {{ label }}
  </button>
</template>