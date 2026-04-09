<script setup>
import { reactive, ref, computed } from 'vue'

const form = reactive({
  fullName: '',
  studentId: '',
  email: '',
  password: '',
  program: '',
  track: '',
  year: '',
  bio: '',
  agree: false
})

const errors = reactive({})
const showModal = ref(false)
const submitted = ref(false)

const bioMaxLength = 200
const bioRemaining = computed(() => form.bio.length)

const yearOptions = [
  { value: '1', label: 'Year 1', desc: 'Beginner student level' },
  { value: '2', label: 'Year 2', desc: 'Intermediate foundation' },
  { value: '3', label: 'Year 3', desc: 'Project-focused stage' },
  { value: '4', label: 'Year 4', desc: 'Internship or capstone stage' },
]

// VALIDATION
function validate() {
  errors.fullName  = form.fullName  ? '' : 'Full name is required.'
  errors.studentId = form.studentId ? '' : 'Student ID is required.'
  errors.email     = form.email     ? '' : 'Email is required.'
  errors.password  = form.password.length >= 8 ? '' : 'Password is required.'
  errors.program   = form.program   ? '' : 'Please select your program.'
  errors.track     = form.track     ? '' : 'Please choose a workshop track.'
  errors.year      = form.year      ? '' : 'Please select your year level.'
  errors.agree     = form.agree     ? '' : 'You must confirm the information.'
}

const hasAnyError = computed(() =>
  Object.values(errors).some(e => e)
)

// SUBMIT
function handleSubmit() {
  submitted.value = true
  validate()
  if (!hasAnyError.value) {
    showModal.value = true
  }
}

// RESET
function resetForm() {
  Object.assign(form, {
    fullName: '',
    studentId: '',
    email: '',
    password: '',
    program: '',
    track: '',
    year: '',
    bio: '',
    agree: false
  })
  Object.keys(errors).forEach(key => (errors[key] = ''))
  submitted.value = false
}

function closeModal() {
  showModal.value = false
  resetForm()
}
</script>

<template>
  <div class="min-h-screen bg-gray-100 flex items-center justify-center p-6">
    <div class="bg-white rounded-xl shadow-md w-full max-w-3xl p-8">

      <!-- Header -->
      <p class="text-blue-600 text-sm font-medium mb-1">Hands-on Lab</p>
      <h1 class="text-2xl font-bold text-gray-800 mb-1">Student Workshop Registration Form</h1>
      <p class="text-gray-500 text-sm mb-6">
        Practice styling form controls, focus states, and validation feedback with Vue.js and Tailwind CSS.
      </p>

      <form @submit.prevent="handleSubmit" class="space-y-5">

        <!-- Full Name + Student ID -->
        <div class="grid grid-cols-2 gap-4">
          <div>
            <label class="block text-sm font-semibold text-gray-700 mb-1">
              Full Name <span class="text-red-500">*</span>
            </label>
            <input
              v-model="form.fullName"
              type="text"
              placeholder="Enter your full name"
              class="w-full border rounded-lg px-3 py-2 text-sm focus:outline-none focus:ring-2 focus:ring-blue-400"
              :class="errors.fullName ? 'border-red-400 bg-red-50' : 'border-gray-300'"
            />
            <p v-if="errors.fullName" class="text-red-500 text-xs mt-1">{{ errors.fullName }}</p>
          </div>
          <div>
            <label class="block text-sm font-semibold text-gray-700 mb-1">
              Student ID <span class="text-red-500">*</span>
            </label>
            <input
              v-model="form.studentId"
              type="text"
              placeholder="e.g. 6601234567"
              class="w-full border rounded-lg px-3 py-2 text-sm focus:outline-none focus:ring-2 focus:ring-blue-400"
              :class="errors.studentId ? 'border-red-400 bg-red-50' : 'border-gray-300'"
            />
            <p v-if="errors.studentId" class="text-red-500 text-xs mt-1">{{ errors.studentId }}</p>
          </div>
        </div>

        <!-- Email + Password -->
        <div class="grid grid-cols-2 gap-4">
          <div>
            <label class="block text-sm font-semibold text-gray-700 mb-1">
              Email <span class="text-red-500">*</span>
            </label>
            <input
              v-model="form.email"
              type="email"
              placeholder="yourname@example.com"
              class="w-full border rounded-lg px-3 py-2 text-sm focus:outline-none focus:ring-2 focus:ring-blue-400"
              :class="errors.email ? 'border-red-400 bg-red-50' : 'border-gray-300'"
            />
            <p v-if="errors.email" class="text-red-500 text-xs mt-1">{{ errors.email }}</p>
          </div>
          <div>
            <label class="block text-sm font-semibold text-gray-700 mb-1">
              Password <span class="text-red-500">*</span>
            </label>
            <input
              v-model="form.password"
              type="password"
              placeholder="At least 8 characters"
              class="w-full border rounded-lg px-3 py-2 text-sm focus:outline-none focus:ring-2 focus:ring-blue-400"
              :class="errors.password ? 'border-red-400 bg-red-50' : 'border-gray-300'"
            />
            <p v-if="errors.password" class="text-red-500 text-xs mt-1">{{ errors.password }}</p>
          </div>
        </div>

        <!-- Program + Workshop Track -->
        <div class="grid grid-cols-2 gap-4">
          <div>
            <label class="block text-sm font-semibold text-gray-700 mb-1">
              Program / Major <span class="text-red-500">*</span>
            </label>
            <select
              v-model="form.program"
              class="w-full border rounded-lg px-3 py-2 text-sm focus:outline-none focus:ring-2 focus:ring-blue-400"
              :class="errors.program ? 'border-red-400 bg-red-50' : 'border-gray-300'"
            >
              <option value="">Select your program</option>
              <option>Information Technology</option>
              <option>Computer Science</option>
              <option>Digital Service Innovation</option>
            </select>
            <p v-if="errors.program" class="text-red-500 text-xs mt-1">{{ errors.program }}</p>
          </div>
          <div>
            <label class="block text-sm font-semibold text-gray-700 mb-1">
              Workshop Track <span class="text-red-500">*</span>
            </label>
            <select
              v-model="form.track"
              class="w-full border rounded-lg px-3 py-2 text-sm focus:outline-none focus:ring-2 focus:ring-blue-400"
              :class="errors.track ? 'border-red-400 bg-red-50' : 'border-gray-300'"
            >
              <option value="">Select a track</option>
              <option>Frontend UI Development</option>
              <option>Backend API Design</option>
              <option>UX/UI Design</option>

            </select>
            <p v-if="errors.track" class="text-red-500 text-xs mt-1">{{ errors.track }}</p>
          </div>
        </div>

        <!-- Year Level — Selectable Cards -->
        <div>
          <label class="block text-sm font-semibold text-gray-700 mb-2">
            Year Level <span class="text-red-500">*</span>
          </label>
          <div class="grid grid-cols-4 gap-3">
            <label
              v-for="y in yearOptions"
              :key="y.value"
              class="border rounded-lg p-3 cursor-pointer transition-all"
              :class="
                form.year === y.value
                  ? 'border-blue-500 bg-blue-50 ring-1 ring-blue-500'
                  : errors.year
                  ? 'border-red-300'
                  : 'border-gray-200 hover:border-gray-400'
              "
            >
              <input type="radio" :value="y.value" v-model="form.year" class="hidden" />
              <div class="flex items-start justify-between">
                <span class="text-sm font-semibold text-gray-800">{{ y.label }}</span>
                <span
                  class="w-4 h-4 rounded-full border-2 flex-shrink-0 mt-0.5"
                  :class="
                    form.year === y.value
                      ? 'border-blue-500 bg-blue-500'
                      : 'border-gray-300'
                  "
                ></span>
              </div>
              <p class="text-xs text-gray-400 mt-1 leading-snug">{{ y.desc }}</p>
            </label>
          </div>
          <p v-if="errors.year" class="text-red-500 text-xs mt-1">{{ errors.year }}</p>
        </div>

        <!-- Short Bio with Character Counter -->
        <div>
          <label class="block text-sm font-semibold text-gray-700 mb-1">Short Bio</label>
          <textarea
            v-model="form.bio"
            :maxlength="bioMaxLength"
            rows="4"
            placeholder="Tell us about your interests..."
            class="w-full border border-gray-300 rounded-lg px-3 py-2 text-sm resize-y focus:outline-none focus:ring-2 focus:ring-blue-400"
          ></textarea>
          <div class="flex justify-between items-center mt-1">
            <p class="text-xs text-gray-400">Optional: briefly describe your interests or previous experience.</p>
            <p class="text-xs text-gray-400">{{ bioRemaining }} / {{ bioMaxLength }}</p>
          </div>
        </div>

        <!-- Confirm Checkbox -->
        <div>
          <label class="flex items-start gap-2 cursor-pointer">
            <input
              type="checkbox"
              v-model="form.agree"
              class="mt-0.5 accent-blue-600"
            />
            <span class="text-sm text-gray-700">
              I confirm that the information provided is correct and I agree to participate in the workshop activities.
            </span>
          </label>
          <p v-if="errors.agree" class="text-red-500 text-xs mt-1">{{ errors.agree }}</p>
        </div>

        <!-- Footer: Tip + Buttons -->
        <div class="flex items-center justify-between pt-2 border-t border-gray-100 mt-4">
          <p class="text-xs text-gray-400">
            <span class="font-semibold text-gray-500">Tip:</span>
            Try submitting with empty fields to test validation feedback.
          </p>
          <div class="flex gap-3">
            <button
              type="button"
              @click="resetForm"
              class="px-4 py-2 text-sm border border-gray-300 rounded-lg text-gray-700 hover:bg-gray-50 transition"
            >
              Reset Form
            </button>
            <button
              type="submit"
              class="px-5 py-2 text-sm rounded-lg text-white font-medium transition"
              :class="form.agree ? 'bg-blue-600 hover:bg-blue-700' : 'bg-gray-300 cursor-not-allowed'"
            >
              Submit Registration
            </button>
          </div>
        </div>

      </form>
    </div>

    <!-- Success Modal -->
    <Transition name="fade">
      <div
        v-if="showModal"
        class="fixed inset-0 bg-black bg-opacity-40 flex items-center justify-center z-50"
      >
        <div class="bg-white rounded-2xl shadow-xl p-8 w-80 text-center">
          <!-- Green checkmark circle -->
          <div class="w-14 h-14 rounded-full bg-green-100 flex items-center justify-center mx-auto mb-4">
            <svg class="w-7 h-7 text-green-500" fill="none" stroke="currentColor" stroke-width="3" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7" />
            </svg>
          </div>
          <h2 class="text-xl font-bold text-gray-800 mb-2">Registration Submitted</h2>
          <p class="text-gray-500 text-sm mb-6">Your workshop registration has been recorded successfully.</p>
          <button
            @click="closeModal"
            class="w-full bg-green-500 hover:bg-green-600 text-white font-semibold py-2 rounded-lg transition"
          >
            Close
          </button>
        </div>
      </div>
    </Transition>

  </div>
</template>

<style scoped></style>