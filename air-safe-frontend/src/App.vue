<script setup>
import { ref } from 'vue'
import Header from '@/components/header2.vue'
import SecondSection from '@/components/Second section.vue'
import ThirdSection from '@/components/Third section.vue'
import FleetAccessSection from '@/components/Global fleet Access.vue'


const heroTitle = ref('Private Jet Charter Worldwide.')
const heroSubtitle = ref('Access Jet Group offers a smarter alternative to private jet membership programs , an on-demand private jet charter service that provides access to a global fleet of private aie with global access ,no contracts, and no-restritions.')

const handleExplore = () => {
  console.log("Requesting a flight...")
}
</script>

<template>
  <div id="app">
    <div class="app-content">
      <Header :heroTitle="heroTitle" :heroSubtitle="heroSubtitle" />
      <SecondSection />
      <ThirdSection />
      <FleetAccessSection />
    </div>
  </div>
</template>


<style>
#app {
  width: 100vw;
  height: 100vh;
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  background: #fff;
  box-sizing: border-box;
  overflow-y: auto;
}

.app-content {
  width: 100%;
  max-width: 100%;
  padding: 0;
  box-sizing: border-box;
  min-height: 100vh;
}

@media (max-width: 430px) {
  .app-content {
    padding: 0;
  }
}

section {
  scroll-margin-top: 40px;
}
</style>