<template>
  <section 
    class="relative w-full py-24 px-6 bg-cover bg-center bg-no-repeat overflow-x-hidden flex items-center"
    :style="{ backgroundImage: `url(${jetBackground})` }"
  >
    <div class="absolute inset-0 bg-white/40 backdrop-blur-sm"></div>

    <div class="relative z-10 max-w-7xl mx-auto w-full">
      
      <!-- Flex row with 20px gap -->
      <div 
        ref="trigger"
        class="flex flex-row flex-wrap justify-center items-stretch w-full mb-16"
        style="gap: 20px;" 
      >
        <div 
          v-for="(card, index) in cards" 
          :key="card.title"
          class="flex-1 `min-w-75` p-8 bg-white/30 backdrop-blur-md border border-white/50 rounded-sm shadow-sm transition-all duration-1000 ease-[cubic-bezier(0.2,1,0.3,1)]"
          :class="[
            isVisible ? 'opacity-100 translate-x-0' : getInitialState(index)
          ]"
        >
          <div class="flex flex-col h-full text-center">
            <h5 class="text-slate-900 text-[11px] font-black tracking-[0.4em] mb-4 uppercase">
              {{ card.title }}
            </h5>
            <!-- Standard lowercase p tag -->
            <p class="text-slate-900 text-sm leading-relaxed font-light wrap-break-word">
              {{ card.text }}
            </p>
          </div>
        </div>
      </div>

      <div class="max-w-2xl text-center mx-auto">
        <p class="text-slate-900 text-lg font-light italic mb-8">
          "Uncompromising service, worldwide accessibility."
        </p>
        <button class="bg-black text-white p-3 px-10 text-[10px] font-bold uppercase tracking-[0.2em] hover:bg-slate-800 transition-all">
          LEARN MORE →
        </button>
      </div>

    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import jetBackground from '@/assets/BBJ-Select-737-7-FWD_lounge_B_serene.jpg'

const isVisible = ref(false)
const trigger = ref(null)

const cards = [
  {
    title: 'TAILORED SOLUTION',
    text: 'Private air solutions are at the core of our business. We design bespoke travel experiences tailored to your itinerary.'
  },
  {
    title: '24/7 SUPPORT',
    text: 'Direct access to a dedicated charter professional, available day and night, 365 days a year for your convenience.'
  },
  {
    title: 'GLOBAL SERVICE',
    text: 'With a preferred network spanning the globe, we arrange private flights anywhere in the world at any time.'
  }
]

const getInitialState = (index) => {
  if (index === 0) return 'opacity-0 -translate-x-[100px]' 
  if (index === 1) return 'opacity-0 scale-95'           
  if (index === 2) return 'opacity-0 translate-x-[100px]'  
}

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    if (entries[0].isIntersecting) {
      isVisible.value = true
    }
  }, { threshold: 0.1 })

  if (trigger.value) observer.observe(trigger.value)
})
</script>