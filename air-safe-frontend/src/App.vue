<script setup>
import { ref } from 'vue'
import Header from '@/components/header2.vue'
import SecondSection from '@/components/Second section.vue'



const heroTitle = ref('Private Jet Charter Worldwide.')
const heroSubtitle = ref('Access Jet Group offers a smarter alternative to private jet membership programs , an on-demand private jet charter service that provides access to a global fleet of private aie with global access ,no contracts, and no-restritions.')

const handleExplore = () => {
  console.log("Requesting a flight...")
}
</script>

<template>
  <div>
    <Header :heroTitle="heroTitle" :heroSubtitle="heroSubtitle" />
    <SecondSection />
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