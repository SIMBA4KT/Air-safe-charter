<template>
  <div
    class="relative w-full py-24 px-6 bg-cover bg-center bg-no-repeat flex flex-col items-center"
    :style="{ backgroundImage: `url(${jetBackground})` }"
  >
    <!-- Section 1: Cards above the background image -->
    <section class="cards-section max-w-7xl mx-auto w-full px-6 mb-[40px]">
      <div ref="trigger" class="cards-grid w-full items-stretch">
        <div
          v-for="(card, index) in cards"
          :key="card.title"
          class="card h-full p-[15px] backdrop-blur-md border rounded-sm transition-all duration-1000 ease-[cubic-bezier(0.2,1,0.3,1)] flex flex-col justify-between"
          :class="[
            isVisible
              ? 'opacity-100 translate-x-0 scale-100'
              : getInitialState(index),
          ]"
        >
          <div class="flex flex-col h-full text-center">
            <h5
              class="card-title text-[11px] font-black tracking-[0.4em] mb-4 uppercase"
            >
              {{ card.title }}
            </h5>
            <p
              class="card-text text-sm leading-relaxed font-light break-words m-0"
            >
              {{ card.text }}
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- Section 2: Background Image Section -->
    <section
      class="relative w-full py-24 px-6 bg-cover bg-center bg-no-repeat flex items-center"
      :style="{ backgroundImage: `url(${jetBackground})` }"
    >
      <div class="absolute inset-0 bg-white/40 backdrop-blur-sm"></div>

      <div class="relative z-10 max-w-2xl text-center mx-auto">
        <p class="text-slate-900 text-lg font-light italic mb-8">
          "Uncompromising service, worldwide accessibility."
        </p>
        <button
          class="bg-black text-white p-3 px-10 text-[10px] font-bold uppercase tracking-[0.2em] hover:bg-slate-800 transition-all"
        >
          LEARN MORE &rarr;
        </button>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import jetBackground from "@/assets/BBJ-Select-737-7-FWD_lounge_B_serene.jpg";

const isVisible = ref(false);
const trigger = ref(null);

const cards = [
  {
    title: "TAILORED SOLUTION",
    text: "Private air solutions are at the core of our business. We design bespoke travel experiences tailored to your itinerary.",
  },
  {
    title: "24/7 SUPPORT",
    text: "Direct access to a dedicated charter professional, available day and night, 365 days a year for your convenience.",
  },
  {
    title: "GLOBAL SERVICE",
    text: "With a preferred network spanning the globe, we arrange private flights anywhere in the world at any time.",
  },
];

const getInitialState = (index) => {
  if (index === 0) return "opacity-0 -translate-x-[100px]";
  if (index === 1) return "opacity-0 scale-95";
  if (index === 2) return "opacity-0 translate-x-[100px]";
};

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      if (entries[0].isIntersecting) {
        isVisible.value = true;
        observer.disconnect();
      }
    },
    { threshold: 0.1 },
  );

  if (trigger.value) observer.observe(trigger.value);
});
</script>

<style scoped>
.cards-grid {
  display: flex;
  justify-content: space-around;
  align-items: stretch;
  padding: 35px;
}

.card {
  flex: 0 1 calc(33.333% - 30px);
  width: calc(33.333% - 30px);
  color: #27313d;
  background: rgba(255, 255, 255, 0.12);
  border-color: rgba(255, 255, 255, 0.65);
  box-shadow: 0 12px 28px rgba(15, 23, 42, 0.08);
  transition-property: transform, background-color, border-color, box-shadow;
}

.card-title {
  color: #263342;
  transition: color 0.25s ease;
}

.card-text {
  color: #334155;
  transition: color 0.25s ease;
}

.card:hover {
  background: rgba(15, 23, 42, 0.78);
  border-color: #e8c98f;
  box-shadow: 0 18px 36px rgba(15, 23, 42, 0.26);
  transform: translateY(-6px);
}

.card:hover .card-title {
  color: #f3d39a;
}

.card:hover .card-text {
  color: #f8fafc;
}

@media (max-width: 700px) {
  .cards-grid {
    flex-direction: column;
    gap: 1rem;
  }

  .card {
    width: 100%;
  }
}
</style>
