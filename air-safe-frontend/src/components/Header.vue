<template>
  <nav 
    :class="[
      'fixed top-0 left-0 w-full z-50 transition-all duration-300 flex items-center',
      'h-[40px] border-b',
      isScrolled ? 'bg-white shadow-md border-gray-200' : 'bg-white border-transparent'
    ]"
  >
    <div class="w-full px-4 flex items-center justify-between gap-4">
      
      <div class="flex items-center gap-2 cursor-pointer shrink-0" @click="scrollToTop">
        <div class="w-7 h-7 bg-blue-600 rounded-md flex items-center justify-center">
          <span class="text-[10px] text-white font-black italic">AS</span>
        </div>
        <h1 class="text-blue-600 font-black text-sm tracking-tight hidden sm:block">
          AIR-SAFE <span class="text-gray-400 font-light italic">TRAVELLERS</span>
        </h1>
      </div>

      <ul class="hidden lg:flex items-center gap-2">
        <li v-for="link in navLinks" :key="link.name">
          <a 
            :href="link.href" 
            class="px-4 py-1.5 rounded-lg bg-blue-50 text-blue-700 text-[10px] font-bold uppercase tracking-wider hover:bg-blue-600 hover:text-white transition-all cursor-pointer whitespace-nowrap"
          >
            {{ link.name }}
          </a>
        </li>
      </ul>

      <div class="flex items-center gap-3 shrink-0">
        <div class="hidden md:flex items-center border border-blue-200 rounded-full px-3 py-1 bg-gray-50 group hover:border-blue-500 transition-colors">
          <span class="text-blue-400 mr-2">🔍</span>
          <button class="text-[9px] font-bold text-gray-500 uppercase tracking-widest cursor-pointer">
            Enquire Now
          </button>
        </div>

        <div class="w-7 h-7 bg-gray-100 rounded-full flex items-center justify-center cursor-pointer hover:bg-blue-100 transition-colors">
          <span class="text-xs">👤</span>
        </div>

        <button @click="isMenuOpen = !isMenuOpen" class="lg:hidden p-1 text-blue-600 cursor-pointer">
          {{ isMenuOpen ? '✕' : '🍃' }}
        </button>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isMenuOpen = ref(false)
const isScrolled = ref(false)

const handleScroll = () => {
  isScrolled.value = window.scrollY > 10
}

const scrollToTop = () => {
  window.scrollTo({ top: 0, behavior: 'smooth' })
}

onMounted(() => window.addEventListener('scroll', handleScroll))
onUnmounted(() => window.removeEventListener('scroll', handleScroll))

const navLinks = [
  { name: 'Buy', href: '#services' },
  { name: 'Models', href: '#models' },
  { name: 'Services', href: '#destinations' },
  { name: 'Destinations', href: '#blog' },
  { name: 'About Us', href: '#commitment' },
]
</script>