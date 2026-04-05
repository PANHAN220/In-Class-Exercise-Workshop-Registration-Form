<script setup>
defineProps(['badge', 'title', 'desc'])
</script>

<template>
  <div class="bg-white p-5 rounded-2xl border border-gray-200 shadow-sm">
    <div class="flex justify-between items-center mb-3">
      <span class="text-xs bg-blue-100 text-blue-600 px-2 py-1 rounded-full">
        {{ badge }}
      </span>
      <span class="text-xs text-gray-400">
        Reusable
      </span>
    </div>

    <!-- Title -->
    <h3 class="font-semibold text-lg mb-2">
      {{ title }}
    </h3>

    <!-- Description -->
    <p class="text-sm text-gray-500 mb-4">
      {{ desc }}
    </p>

    <!-- Button -->
    <button class="border px-3 py-1.5 rounded-lg text-sm hover:bg-gray-100">
      View Details
    </button>

  </div>
</template>