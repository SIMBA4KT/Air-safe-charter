<script setup>
import { ref } from 'vue'

import Header from '@/components/Header.vue'
import MainSection from '@/components/Main section.vue'
import SecondSection from '@/components/Second section.vue'
import ThirdSection from '@/components/Third section.vue'


const heroTitle = ref('Private Jet Charter Worldwide.')
const heroSubtitle = ref('Access Jet Group offers a smarter alternative to private jet membership programs , an on-demand private jet charter service that provides access to a global fleet of private aie with global access ,no contracts, and no-restritions.')

const handleExplore = () => {
  console.log("Requesting a flight...")
}
</script>

<template>
  <div>
    <section class="relative w-full h-[80vh] flex items-center justify-center">
      <img src="@/assets/BBJ-Select-737-7-FWD_lounge_A_serene.jpg" class="absolute inset-0 w-full h-full object-cover" />
      <img src="@/assets/AJG-logo-11.webp" alt="Logo" class="absolute top-4 left-4 w-12 h-12 z-20" />

      <div class="relative z-10 text-center space-y-8">
        <Header />
        <h1 class="text-white text-5xl font-bold">{{ heroTitle }}</h1>
        <p class="text-gray-200 mt-4">{{ heroSubtitle }}</p>
        <button @click="handleExplore" class="mt-8 bg-amber-500 px-8 py-3 rounded-full">
          REQUEST A FLIGHT 
        </button>
      </div>
    </section>

    <MainSection />
    <SecondSection />
    <ThirdSection />
  </div>
</template>


<style>
#app {
  margin: 0;
  padding: 0;
}

section {
  scroll-margin-top: 40px;
} 

</style>