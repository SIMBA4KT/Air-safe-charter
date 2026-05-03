<script setup>
import { ref } from 'vue'
import MainSection from './Main section.vue'

const props = defineProps({
  heroTitle: String,
  heroSubtitle: String
})

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

      <!-- Hero Title and Subtitle -->
      <div class="hero-content">
        <h1 class="hero-title">{{ heroTitle }}</h1>
        <p class="hero-subtitle">{{ heroSubtitle }}</p>
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

@media (max-width: 430px) {
  .main-header {
    flex-direction: column;
    align-items: stretch;
    justify-content: flex-start;
    height: auto;
    padding: 1rem 0.75rem 0.5rem;
  }

  .logo-wrapper,
  .nav-links,
  .action-wrapper {
    width: 100%;
    justify-content: center;
  }

  .nav-links {
    order: 2;
    gap: 0.5rem;
    margin-top: 0.8rem;
  }

  .action-wrapper {
    order: 3;
    margin-top: 0.75rem;
  }

  .hero-content {
    position: static;
    transform: none;
    text-align: center;
    max-width: 100%;
    width: 100%;
    margin: 1rem 0 0;
    padding: 0 0.5rem;
  }

  .hero-title {
    font-size: 2rem;
  }

  .hero-subtitle {
    font-size: 0.95rem;
  }

  .booking-interface {
    position: static;
    width: 100%;
    padding: 0 0.75rem 1rem;
    margin-top: 1.25rem;
  }

  .main-header {
    gap: 0.75rem;
  }

  .header-bg {
    min-height: 420px;
  }

  .header-bg img {
    object-position: center;
  }
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

.hero-content {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
  color: white;
  z-index: 10;
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  max-width: 80%;
}

.hero-title {
  font-size: 3rem;
  font-weight: bold;
  margin: 0;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
}

.hero-subtitle {
  font-size: 1rem;
  margin: 0.5rem 0 0 0;
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
}

.booking-interface {
  position: absolute;
  bottom: 20px;
  left: 0;
  right: 0;
  padding: 0 2rem;
  z-index: 15;
}
</style>
