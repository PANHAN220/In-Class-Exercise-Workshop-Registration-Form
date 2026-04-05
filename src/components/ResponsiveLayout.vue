<script setup></script>

<template>
  <div class="grid md:grid-cols-3 gap-4 ">
    

    <div class="bg-gray-100 p-5 rounded-2xl md:col-span-2 ">
        <h3 class="font-semibold mb-2">Main Content Area</h3>
        <p class="text-gray-600 text-sm">
            This area can be used for dashboard content, a feature section, course details, or product descriptions.
            It demonstrates a simple reusable container pattern with consistent padding, rounded corners, and spacing.
        </p>
    </div>

    <!-- Right -->
    <div class="bg-blue-600 text-white p-5  rounded-2xl md:col-span-1">
       <h3 class="font-semibold mb-2">Summary Panel</h3>
        <p class="text-sm mb-4">
            This panel can be reused for quick stats, announcements, or call-to-action content.</p>
        <button class="bg-white text-blue-600 px-4 py-2 rounded-lg text-sm hover:bg-gray-200">
            Learn More
        </button>
    </div>

  </div>
</template>