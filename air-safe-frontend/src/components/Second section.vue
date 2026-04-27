<script setup>
import { ref } from 'vue'

</script>

<template>
    <div>
        <h6 class="text-2xl font-bold text-slate-900">ABOUT US</h6>
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
        <button class="mt-4 bg-amber-500 hover:bg-amber-600 text-slate-900 font-bold px-6 py-3 rounded-lg transition-all transform hover:scale-105">
            DISCOVER MORE ABOUT US
        </button>
    </div>
    <div>
        <img src = "@/assets/BoeingMainFront.jpg" alt="Boeing Main Front" class="w-full h-auto rounded-lg shadow-lg mt-6">
    </div>
</template>

<style scoped>
h2 {
    font-size: 1.5rem;
    font-weight: 600;
    color: #1e293b; /* slate-900 */
    margin-top: 0.5rem;
}
p {
    font-size: 1rem;
    color: #475569; /* slate-700 */
    margin-top: 0.5rem;
}
</style>