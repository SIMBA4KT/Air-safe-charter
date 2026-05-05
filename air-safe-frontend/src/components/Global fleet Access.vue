<template>
  <div class="scroll-container">
    <!-- Helper spacer to allow scrolling at the start -->
    <div class="spacer">GLOBAL FLEET ACCESS
        <h1>Global Access to Every Type of Fleet</h1>
    <p>Access Jet Group ensures the right solution for every trip, anywhare inthe world.Our fleet access covers every aircraft cayegory, giving you the flexibility to choose exactly what suits your journey.</p>
    </div>

    <div
      v-for="(row, index) in rows"
      :key="index"
      class="row-container"
      :class="{ 'is-visible': visibleRows.includes(index) }"
      :data-index="index"
      ref="rowRefs"
    >
      <div class="box left-box">
            <img :src="row.left.image" alt="" />
            <h3>{{ row.left.title }}</h3>
            <p>{{ row.left.text }}</p>
      </div>
      <div class="box right-box">
        <img :src="row.right.image" alt="" />
        <h3>{{ row.right.title }}</h3>
        <p>{{ row.right.text }}</p>
      </div>
    </div>

    <div class="spacer">Safety Is Our Highest Priority</div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const rows = [
  { left: { title: 'LIGHT JETS', text: '(4-6 passengers)- Compact,efficient,perfect for short trips.', image: '@/assets/image1.jpg' } ,
    right: {title: 'MIDSIZE JETS', text: '(6-8 passengers)- Balanced performance and comfort.', image: '@/assets/image2.jpg' } },
  { left: { title: 'SUPER MIDSIZE JETS', text: '(8-9 passengers)- Spacious with longer endurance.', image: '@/assets/BoeingMainFront.png' },
    right: { title: 'LARGE & HEAVYJETS', text: '(8-16 passengers)- Maximum comfort and luxury for long-distance travel.', image: '@/assets/image4.jpg' } },
  { left: { title: 'TURBOPROPS', text: '(4-8 passengers)- Versatile, ideal for short runways and regional travel.', image: '@/assets/image5.jpg' },
    right: { title: 'VIP AIRLINERS', text: '(20+ passengers)- Ultimate luxury and space for large groups or special occasions.', image: '@/assets/airplaneTop.png' } }
]
const visibleRows = ref([])
const rowRefs = ref([])

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      const index = parseInt(entry.target.getAttribute('data-index'))
      if (entry.isIntersecting) {
        if (!visibleRows.value.includes(index)) {
          visibleRows.value.push(index)
        }
      }
    })
  }, { threshold: 0.2 })

  rowRefs.value.forEach((el) => observer.observe(el))
})
</script>

<style scoped>
.scroll-container {
  overflow-x: hidden;
}

.spacer {
  height: 250px;
  display: flex;
  align-items: top;
  justify-content: center;
  font-size: 0.9rem;
  background: #f4f4f4;
}

.row-container {
  display: flex;
  justify-content: center;
  gap: 20px;
  margin: 50px 0;
  perspective: 1000px;
}

.box {
  width: 490px;
  height:150px;
  background-color: #f4faf7;
  color: #170250;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: light;
  font-size: 0.9rem;
  transition: transform 0.8s ease-out, opacity 0.8s ease-out;
  opacity: 0;
}

/* Starting positions */
.left-box {
  transform: translateX(-150%);
}

.right-box {
  transform: translateX(150%);
}

.is-visible .left-box,
.is-visible .right-box {
  transform: translateX(0);
  opacity: 1;
}

.right-box {
  background-color: hsl(210, 11%, 96%);

}
.box img {
  width: 160px;
  height: 100px;
  border-radius: 0.75rem;
  margin-bottom: 0.75rem;;
}

.box-text {
  text-align: center;
  text-wrap: wrap;
}
</style>