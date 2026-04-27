<script setup>
import { ref } from 'vue'

const searchData = ref({
  tripType: 'One Way',
  from: '',
  to: '',
  departure: '',
  passengers: 1
})
</script>

<template>
  <div class="bg-slate-900 p-6 rounded-lg shadow-2xl max-w-7xl mx-auto">
    <div class="flex flex-col lg:flex-row items-center gap-2 bg-white p-2 rounded-xl">
      
      <button class="w-full lg:w-auto px-6 py-4 text-sm font-bold text-slate-700 hover:bg-gray-100 rounded-lg transition border-r border-gray-200">
        TRIP TYPE
      </button>

      <div class="flex flex-1 w-full border-r border-gray-200">
        <button class="flex-1 px-6 py-4 text-left text-sm font-bold text-slate-700 hover:bg-gray-100 rounded-l-lg transition">
          FROM
        </button>
        <div class="w-1px bg-gray-200 my-2"></div> <button class="flex-1 px-6 py-4 text-left text-sm font-bold text-slate-700 hover:bg-gray-100 rounded-r-lg transition">
          TO
        </button>
      </div>

      <button class="w-full lg:w-auto px-6 py-4 text-sm font-bold text-slate-700 hover:bg-gray-100 rounded-lg transition border-r border-gray-200">
        DEPARTURE
      </button>

      <button class="w-full lg:w-auto px-6 py-4 text-sm font-bold text-slate-700 hover:bg-gray-100 rounded-lg transition border-r border-gray-200">
        TRIP TYPE
      </button>

      <button class="w-full lg:w-auto px-6 py-4 text-sm font-bold text-slate-700 hover:bg-gray-100 rounded-lg transition">
        PASSENGERS
      </button>

      <button class="w-full lg:w-auto bg-amber-500 hover:bg-amber-600 text-slate-900 font-black px-8 py-4 rounded-lg transition-all transform hover:scale-105 shadow-md">
        SHOW ESTIMATES
      </button>

    </div>
  </div>
</template>