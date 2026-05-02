<script setup>
import { ref } from 'vue'
</script>

<template>
    <div class="second-section">
        <div class="content-wrapper">
            <div class="text-content">
                <h6 class="text-2xl font-bold text-slate-900 text-left">ABOUT US</h6>
                <h2>A Boutique Approach to Private Aviation</h2>
                <p>
                    There is an intelligence and luxurious alternative within private air charter.
                    Access Jet Group. Our boutique firm prides itself on delivering a personal approach
                    to select tier of clientele who require and appreciate a discerning global travel experience.
                </p>
                <p>
                    We create custom on-demand charter solutions for both businesses and individuals, serving some of the world's most sophisticated flyers across multiple industries.
                    Every flight is tailored to your unique needs, with no membership fees, blackout dates, or long-term commitments.
                </p>
                <p>
                    Our business model is simple: we're ready when you are. With countless domestic and international destinations, Access Jet Group makes private air travel more flexible,
                    accessible, and personal than ever before.
                </p>
                <button class="mt-4 bg-amber-500 text-white font-bold px-6 py-3 rounded-lg transition-all transform hover:scale-105">
                    DISCOVER MORE ABOUT US
                </button>
            </div>
            <div class="image-content">
                <img src="@/assets/BoeingMainFront.jpg" alt="Boeing Main Front" class="section-image">
            </div>
        </div>
    </div>
</template>

<style scoped>
.second-section {
  padding: 2rem;
  width: 100%;
}

.content-wrapper {
  display: flex;
  gap: 3rem;
  align-items: flex-start;
  width: 100%;
}

.text-content {
  flex: 1;
  text-align: left;
}

.image-content {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}

.section-image {
  width: 100%;
  max-width: 500px;
  height: 350px;
  border-radius: 0.5rem;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
}

h6 {
    font-size: 0.75rem;
    font-weight: 700;
    text-transform: uppercase;
    color: #334155;
}

h2 {
    font-size: 2rem;
    font-weight: 800;
    color: #1e293b; /* slate-900 */
    margin-top: 0.5rem;
}

p {
    font-size: 1rem;
    color: #475569; /* slate-700 */
    margin-top: 0.5rem;
    line-height: 1.6;
}

button {
    width: 100%;
    padding: 0.75rem 1.5rem;
    transition: all 0.2s ease;
    font-size: 1rem;
    font-weight: bold;
}

button:hover {
    transform: translateY(-2px);
}
</style>