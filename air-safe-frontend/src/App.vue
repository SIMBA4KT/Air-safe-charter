<script setup>
import { ref } from 'vue'

import Header from '@/components/Header.vue'

const heroTitle = ref('Private Jet Charter Worldwide.')
const heroSubtitle = ref('Access Jet Group offers a smarter alternative to private jet membership programs , an on-demand private jet charter service that provides access to a global fleet of private aie with global access ,no contracts, and no-restritions.')

const handleExplore = () => {
  console.log("Requesting a flight...")
}
import MainSection from '@/components/Main section.vue'
</script>

<template>
  <div>
    <Header />

    <section class="relative w-full h-[80vh] flex items-center justify-center pt-24">
      <img src="@/assets/BBJ-Select-737-7-FWD_lounge_A_serene.jpg" class="absolute inset-0 w-full h-full object-cover" />

      <div class="relative z-10 text-center space-y-8">
        <h1 class="text-white text-5xl font-bold">{{ heroTitle }}</h1>
        <p class="text-gray-200 mt-4">{{ heroSubtitle }}</p>
        <MainSection />
        <button @click="handleExplore" class="mt-8 bg-amber-500 px-8 py-3 rounded-full">
          REQUEST A FLIGHT 
        </button>
      </div>
    </section>
  </div>
</template>


<style>
/* Any global or extra CSS goes here (optional) */
</style>