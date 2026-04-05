<script setup>
defineProps(['title', 'message', 'class'])
</script>

<template>
  <div :class="['p-4 my-4 rounded-xl', $props.class]">
    
    <h3 class="font-semibold">
      {{ title }}
    </h3>

    <p class="text-sm mt-1">
      {{ message }}
    </p>

  </div>
</template>