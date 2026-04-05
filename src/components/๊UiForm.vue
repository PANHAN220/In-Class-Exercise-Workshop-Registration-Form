<script setup>
import { reactive } from 'vue'

const form = reactive({
    name: '',
    email: '',
    role: '',
    message: ''

})
</script>

<template>
    <div class="space-y-4">

        <div class="grid md: grid-cols-2 gap-4">
            <div>
                <label class="block text-sm font-medium mb-1">Fullname</label>
                <input
                    v-model="form.name"
                    type="text"
                    placeholder="Enter your full name"
                    class="w-full border border-gray-200 rounded-lg px-3 py-2 text-sm focus:outline-none focus:ring-2 focus:ring-blue-300">
                    <p class="text-xs text-gray-400 mt-1">Use a clear and complete student name.</p>
            </div>

            <div>
                <label class="block text-sm font-medium mb-1">Email Address</label>
                <input
                    v-model="form.email"
                    type="email"
                    placeholder="Enter your email"
                    class="w-full border border-gray-200 rounded-lg px-3 py-2 text-sm focus:outline-none focus:ring-2 focus:ring-blue-300"
                    />
                    <p class="text-xs text-gray-400 mt-1">Example: student@mail.kmutt.ac.th</p>
            </div>
        </div>

        <!-- role -->
        <div>
            <label class="block text-sm font-medium mb-1">Role</label>
            <select v-model="form.role" class="w-full border border-gray-200 rounded-lg px-3 py-2 text-sm focus:outline-none focus:ring-2 focus:ring-blue-300">
                 <option value="">Select your role</option>
                <option>Student</option>
                <option>Teacher</option>
                <option>Staff</option>
            </select>
        </div>

        <!-- message -->

        <div>
            <label class="block text-sm font-medium mb-1">Message</label>
            <textarea
                v-model="form.message"
                placeholder="Write your message here"
                class="w-full border border-gray-200 rounded-lg px-3 py-2 text-sm h-32 focus:outline-none focus:ring-2 focus:ring-blue-300 resize-y"
            ></textarea>
            <p class="text-xs text-red-500 mt-1">This is an example of validation/helper text styling.</p>
        </div>

        <button class="bg-blue-600 text-white px-5 py-2 rounded-lg text-sm font-medium hover:bg-blue-700">
            Submit Form
        </button>
    </div>

    
</template>