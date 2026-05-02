<script setup>
import { ref } from 'vue'
import MainSection from './Main section.vue'

const activePage = ref(0)
const navPages = ref([
  { id: 0, name: 'SERVICES' },
  { id: 1, name: 'PRIVATE JET MODELS' },
  { id: 2, name: 'DESTINATIONS' },
  { id: 3, name: 'BLOG' },
  { id: 4, name: 'OUR COMMITMENT' }
])

</script>

<template>
  <div class="header-container">
    <header class="main-header">
      
      <!-- 1. Logo -->
      <div class="logo-wrapper">
        <img src="@/assets/logo.png" alt="AirSafe Logo" class="logo-img">
      </div>

      <!-- 2. Navigation Links -->
      <nav class="nav-links">
        <div 
          v-for="page in navPages" 
          :key="page.id"
          @click="activePage = page.id"
          :class="['nav-item', activePage === page.id ? 'active' : '']"
        >
          {{ page.name }}
          <span v-if="['SERVICES', 'DESTINATIONS', 'BLOG', 'OUR COMMITMENT'].includes(page.name)" class="chevron">▾</span>
        </div>
      </nav>
      <!-- 3. Enquire Button -->
      <div class="action-wrapper">
        <button class="enquire-btn">
          ENQUIRE NOW
        </button>
      </div>

      <div class="header-bg">
        <img src="@/assets/BBJ-Select-737-7-FWD_lounge_A_serene.jpg" alt="Background">
      </div>

      <!-- Flight Booking Interface at bottom -->
      <div class="booking-interface">
        <MainSection />
      </div>
    </header>
  </div>
</template>

<style scoped>
.header-container {
  width: 100%;
}

.main-header {
  position: relative;
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  align-items: flex-start;
  justify-content: space-between;
  padding: 0.5rem 2rem;
  width: 100%;
  height: 400px;
  z-index: 10;
  gap: 1rem;
}

.logo-wrapper {
  flex: 0 0 auto;
  display: flex;
  align-items: flex-start;
}

.logo-img {
  height: 60px;
  width: auto;
}

.nav-links {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  justify-content: center;
  flex: 1 1 auto;
  align-items: flex-end;
}

.nav-item {
  cursor: pointer;
  font-size: 0.65rem;
  font-weight: 600;
  color: #d1d5db;
  transition: color 0.3s;
  letter-spacing: 0.5px;
  padding-bottom: 0.25rem;
  white-space: nowrap;
}

.nav-item:hover {
  color: #fbbf24;
}

.nav-item.active {
  color: #fbbf24;
  border-bottom: 2px solid #fbbf24;
}

.chevron {
  margin-left: 0.25rem;
  font-size: 0.5em;
  opacity: 0.6;
  font-weight: 300;
}

.action-wrapper {
  flex: 0 0 auto;
  display: flex;
  align-items: flex-end;
}

.enquire-btn {
  background-color: #fbbf24;
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 50px;
  border: none;
  font-weight: bold;
  cursor: pointer;
  white-space: nowrap;
  transition: background-color 0.3s;
  font-size: 0.7rem;
}

.enquire-btn:hover {
  background-color: #f59e0b;
}

.header-bg {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
  overflow: hidden;
}

.header-bg img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.booking-interface {
  position: absolute;
  bottom: 20px;
  left: 2rem;
  z-index: 15;
}
</style>
