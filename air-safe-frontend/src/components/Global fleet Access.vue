<template>
  <div class="scroll-container">
    <div class="spacer">
      GLOBAL FLEET ACCESS
      <h1>Global Access to Every Type of Fleet</h1>
      <p>
        Access Jet Group ensures the right solution for every trip, anywhare
        inthe world.Our fleet access covers every aircraft cayegory, giving you
        the flexibility to choose exactly what suits your journey.
      </p>
    </div>

    <div class="fleet-grid">
      <div
        v-for="(card, index) in cards"
        :key="card.title"
        class="fleet-card"
        :class="{ 'is-visible': visibleCards.includes(index) }"
        :data-index="index"
        ref="cardRefs"
      >
        <img :src="card.image" :alt="card.title" />
        <div class="card-copy">
          <h3>{{ card.title }}</h3>
          <p>{{ card.text }}</p>
        </div>
      </div>
    </div>

    <div class="spacer">Safety Is Our Highest Priority</div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";

import lightJetImage from "@/assets/BoeingMainFront.jpg";
import midsizeJetImage from "@/assets/airplaneTop.png";
import superMidsizeJetImage from "@/assets/BoeingMainFront.png";
import largeJetImage from "@/assets/BBJ-Select-737-7-FWD_lounge_A_serene.jpg";
import turbopropImage from "@/assets/BBJ-Select-737-7-AFT_lounge_C_serene.jpg";
import vipAirlinerImage from "@/assets/BBJ-Select-737-7-FWD_lounge_B_serene.jpg";

const cards = [
  {
    title: "LIGHT JETS",
    text: "(4-6 passengers) - Compact, efficient, perfect for short trips.",
    image: lightJetImage,
  },
  {
    title: "MIDSIZE JETS",
    text: "(6-8 passengers) - Balanced performance and comfort.",
    image: midsizeJetImage,
  },
  {
    title: "SUPER MIDSIZE JETS",
    text: "(8-9 passengers) - Spacious with longer endurance.",
    image: superMidsizeJetImage,
  },
  {
    title: "LARGE & HEAVY JETS",
    text: "(8-16 passengers) - Maximum comfort and luxury for long-distance travel.",
    image: largeJetImage,
  },
  {
    title: "TURBOPROPS",
    text: "(4-8 passengers) - Versatile, ideal for short runways and regional travel.",
    image: turbopropImage,
  },
  {
    title: "VIP AIRLINERS",
    text: "(20+ passengers) - Ultimate luxury and space for large groups or special occasions.",
    image: vipAirlinerImage,
  },
];

const visibleCards = ref([]);
const cardRefs = ref([]);

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        const index = Number.parseInt(
          entry.target.getAttribute("data-index"),
          10,
        );
        if (entry.isIntersecting && !visibleCards.value.includes(index)) {
          visibleCards.value.push(index);
        }
      });
    },
    { threshold: 0.2 },
  );

  cardRefs.value.forEach((el) => observer.observe(el));
});
</script>

<style scoped>
.scroll-container {
  overflow-x: hidden;
  padding: 2rem 1rem 4rem;
}

.spacer {
  height: 250px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-size: 0.9rem;
  background: #f4f4f4;
  text-align: center;
  padding: 0 1rem;
}

.fleet-grid {
  width: min(1200px, 100%);
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 24px;
  align-items: stretch;
}

.fleet-card {
  background-color: #f4faf7;
  color: #170250;
  border-radius: 12px;
  display: flex;
  flex-direction: column;
  align-items: stretch;
  justify-content: flex-start;
  gap: 1rem;
  padding: 1rem;
  min-height: 260px;
  box-shadow: 0 10px 25px rgba(15, 23, 42, 0.06);
  transition:
    transform 0.8s ease-out,
    opacity 0.8s ease-out,
    box-shadow 0.2s ease;
  opacity: 0;
  transform: translateY(40px);
}

.fleet-card:hover {
  box-shadow: 0 18px 30px rgba(15, 23, 42, 0.12);
}

.fleet-card.is-visible {
  opacity: 1;
  transform: translateY(0);
}

.fleet-card img {
  width: 100%;
  height: 150px;
  border-radius: 0.75rem;
  object-fit: cover;
}

.card-copy {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.card-copy h3 {
  margin: 0;
  font-size: 1.1rem;
  font-weight: 700;
}

.card-copy p {
  margin: 0;
  line-height: 1.5;
  color: #334155;
}

@media (max-width: 900px) {
  .fleet-grid {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }
}

@media (max-width: 640px) {
  .fleet-grid {
    grid-template-columns: 1fr;
  }
}
</style>
