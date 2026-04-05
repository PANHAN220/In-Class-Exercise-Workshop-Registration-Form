<script setup>
import UiAlert from './components/UiAlert.vue';
import UiBadge from './components/UiBadge.vue';
import UiButton from './components/UiButton.vue';
import UiCard from './components/UiCard.vue';
import ResponsiveLayout from './components/ResponsiveLayout.vue';
import UiForm from './components/๊UiForm.vue';


const buttons = [
    { label: "Primary Button", class: "bg-blue-500 text-white rounded-xl"},
    { label: "Secondary Button", class: "bg-gray-600 text-white rounded-xl"},
    { label: "Outline Button", class: "border border-blue-500 text-blue-500 rounded-xl"},
    { label: "Disabled Button", class: "bg-gray-300 text-gray-500 rounded-xl"}
]

const badges = [
  { label: "Success", class: "bg-green-100 text-green-700" },
  { label: "Warning", class: "bg-yellow-100 text-yellow-700" },
  { label: "Error", class: "bg-red-100 text-red-700" },
  { label: "Neutral", class: "bg-gray-200 text-gray-700" }
]

const alerts = [
  {
    title: "Success Alert",
    message: "Your profile has been updated successfully.",
    class: "bg-green-100 text-green-800 border border-green-300"
  },
  {
    title: "Warning Alert",
    message: "Please review the form before submitting.",
    class: "bg-yellow-100 text-yellow-800 border border-yellow-300"
  },
  {
    title: "Error Alert",
    message: "Something went wrong. Please try again later.",
    class: "bg-red-100 text-red-800 border border-red-300"
  }
]


const cards = [
  {
    badge: "New",
    title: "Basic Card",
    desc: "A simple reusable card for general content blocks in a dashboard or landing page."
  },
  {
    badge: "Profile",
    title: "Student Profile Card",
    desc: "A profile summary card showing student status, program, and quick information."
  },
  {
    badge: "Event",
    title: "Event Card",
    desc: "A reusable event component for workshops, seminars, or hackathon activities."
  }
]


</script>

<template>
   <div class="bg-gray-100 min-h-screen p-6">
    <div class="max-w-5xl mx-auto space-y-6">

      <!-- 1. Buttons -->
      <section class="bg-white p-6 rounded-2xl shadow">
        <h2 class="text-xl font-bold mb-4">1. Buttons</h2>
        <p class="mb-4 text-gray-500">Reusable action styles for primary, secondary, outline, and disabled states.</p>
        <div class="flex gap-3">
          <UiButton 
            v-for="button in buttons"
            :key ="button.label"
            :label ="button.label"
            :class="button.class" 
          />
        </div>
      </section>

      <!-- 2. Badges -->
      <section class="bg-white p-6 rounded-2xl shadow">
        <h2 class="text-xl font-bold mb-4">2. Badges</h2>
        <p class="mb-4 text-gray-500">Small reusable labels for category, state, or status indication.</p>
        <UiBadge 
          v-for="badge in badges"
          :key="badge.label"
          :label="badge.label"
          :class="badge.class"/>
      </section>

      <!-- 3. Alerts -->
      <section class="bg-white p-6 rounded-2xl shadow">
        <h2 class="text-xl font-bold mb-4">3. Alerts</h2>
        <p class="text-gray-500 mb-4">Reusable feedback messages for success, warning, and error states.</p>
        <UiAlert
          v-for="alert in alerts"
          :key="alert.title"
          :title="alert.title"
          :message="alert.message"
          :class="alert.class"
        />
      </section>

      <!-- 4. From -->
      <section class="bg-white p-6 rounded-2xl shadow">
        <h2 class="text-xl font-bold mb-4">4. From Controls</h2>
         <p class="text-gray-500 mb-4">Consistent form patterns with labels, helper text, and validation style.</p>
         <UiForm />
      </section>

      <!-- 5. Cards -->
      <section class="bg-white p-6 rounded-2xl shadow">
        <h2 class="text-xl font-bold mb-4">5. Cards</h2>
        <p class="text-gray-500 mb-4">Responsive card layout for reusable content blocks such as event, profile, or product cards.</p>
          <div class="grid md:grid-cols-3 gap-4">
          <UiCard
            v-for="card in cards"
            :key="card.title"
            :badge="card.badge"
            :title="card.title"
            :desc="card.desc"
          />
        </div>
      </section>

      <!-- 6. Responsive Layout -->
      <section class="bg-white p-6 rounded-2xl shadow">
        <h2 class="text-xl font-bold mb-4">6. Responsive Layout</h2>
        <p class="text-gray-500 mb-4">A reusable section layout with content on the left and summary panel on the right.</p>
        <ResponsiveLayout/>
      </section>

    </div>
  </div>
</template>

<style scoped></style>
