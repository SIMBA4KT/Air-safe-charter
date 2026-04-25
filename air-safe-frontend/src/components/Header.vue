<template>
  <header class="fixed top-0 left-0 right-0 z-50 flex items-center justify-around h-20 bg-slate-900 text-white px-8 shadow-2xl">

    <div class="flex items-center gap-2 cursor-pointer" @click="navigateTo('home')">
      <div class="w-10 h-10 bg-amber-500 rounded-full flex items-center justify-center">
        <span>
          <img src="@/assets/logo.png" alt="Jet Icon" class="w-6 h-6">
        </span>
      </div>
    </div>

    <nav class="hidden md:flex flex-1 justify-around max-w-3xl px-4">
      <div 
        v-for="page in navPages" 
        :key="page.id"
        @click="activePage = page.id"
        :class="[
          'cursor-pointer text-sm font-medium transition-all duration-300 hover:text-amber-400',
          activePage === page.id ? 'text-amber-400 border-b-2 border-amber-400' : 'text-gray-300'
        ]"
      >
        {{ page.name }}
      </div>
    </nav>

    <div class="flex items-center gap-4">
      <button class="bg-amber-500 hover:bg-amber-600 text-slate-900 px-6 py-2 rounded-md font-bold transition-all transform hover:scale-105">
        ENQUIRE NOW
      </button>
    </div>

  </header>
</template>

<script setup>
import { ref } from 'vue'

const navPages = [
  { id: 'services', name: 'SERVICES' },
  { id: 'fleet', name: 'PRIVATE JET MODELS' },
  { id: 'destinations', name: 'DESTINATIONS' },
  { id: 'blog', name: 'BLOG' },
  { id: 'commitment', name: 'OUR COMMIMENT' }
]

const activePage = ref('services')
const navigateTo = (pageId) => {
  activePage.value = pageId
  console.log(`Navigating to: ${pageId}`)
}
</script>