<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const passengerCount = ref(2)

const increasePassengers = () => {
  passengerCount.value++
}

const decreasePassengers = () => {
  if (passengerCount.value > 0) {
    passengerCount.value--
  }
}

const isFocused = ref(false)
const tripType = ref('One Way')

const boxRef = ref(null)

const toggleTripType = (event) => {
  event.stopPropagation()
  tripType.value = tripType.value === 'One Way' ? 'Two Way' : 'One Way'
  isFocused.value = true
}

const handleClickOutside = (event) => {
  if (boxRef.value && !boxRef.value.contains(event.target)) {
    isFocused.value = false
  }
}

onMounted(() => window.addEventListener('click', handleClickOutside))
onUnmounted(() => window.removeEventListener('click', handleClickOutside))
</script>

<template>
  <div class="btn-toolbar" role="toolbar" aria-label="Toolbar with button groups">
    <div class="btn-group" role="group" aria-label="Trip type group">
      <button
        type="button"
        ref="boxRef"
        class="btn custom-input-box"
        :class="{ active: isFocused }"
        @click="isFocused = true"
      >
        <span class="label">TRIP TYPE</span>
        <span v-if="isFocused || tripType" class="value-text">
          {{ tripType }}
        </span>
      </button>
      <button type="button" class="btn btn-secondary btn-icon" @click="toggleTripType">
        <svg width="16" height="16" fill="currentColor" viewBox="0 0 16 16">
          <path fill-rule="evenodd" d="M1.646 4.646a.5.5 0 0 1 .708 0L8 10.293l5.646-5.647a.5.5 0 0 1 .708.708l-6 6a.5.5 0 0 1-.708 0l-6-6a.5.5 0 0 1 0-.708z"/>
        </svg>
      </button>
    </div>
    <div class="btn-group" role="group" aria-label="Second group">
      <button type="button" class="btn btn-secondary">FROM</button>
      <button type="button" class="btn btn-secondary">TO</button>
    </div>
    <div class="btn-group" role="group" aria-label="Third group">
      <button type="button" class="btn btn-secondary grey-btn">DEPARTURE</button>
    </div>
    <div class="btn-group" role="group" aria-label="Passengers group">
      <button type="button" class="btn btn-secondary passenger-input">
        <span class="label">PASSENGERS</span>
        <span class="value-text">{{ passengerCount }}</span>
      </button>
      <button type="button" class="btn btn-secondary grey-btn d-flex flex-column align-items-center">
        <svg width="10" height="10" fill="currentColor" viewBox="0 0 16 16" @click="increasePassengers" style="cursor: pointer;">
          <path fill-rule="evenodd" d="M7.646 4.646a.5.5 0 0 1 .708 0l6 6a.5.5 0 0 0 .708-.708L8.707 3.5 2.354 9.354a.5.5 0 1 1-.708-.708l6-6z"/>
        </svg>
        <svg width="10" height="10" fill="currentColor" viewBox="0 0 16 16" @click="decreasePassengers" style="cursor: pointer;">
          <path fill-rule="evenodd" d="M1.646 4.646a.5.5 0 0 1 .708 0L8 10.293l5.646-5.647a.5.5 0 0 0-.708-.708L8 9.293 2.354 3.646a.5.5 0 0 0-.708.708z"/>
        </svg>
      </button>
    </div>
    <div class="btn-group" role="group" aria-label="Trip type group">
      <button
          type="button"
          ref="boxRef"
          class="btn custom-input-box"
          :class="{ active: isFocused }"
          @click="isFocused = true"
        >
          <span class="label">TRIP TYPE</span>
          <span v-if="isFocused || tripType" class="value-text">
            {{ tripType }}
          </span>
        </button>
        <button type="button" class="btn btn-secondary btn-icon" @click="toggleTripType">
          <svg width="16" height="16" fill="currentColor" viewBox="0 0 16 16">
            <path fill-rule="evenodd" d="M1.646 4.646a.5.5 0 0 1 .708 0L8 10.293l5.646-5.647a.5.5 0 0 1 .708.708l-6 6a.5.5 0 0 1-.708 0l-6-6a.5.5 0 0 1 0-.708z"/>
          </svg>
      </button>
    </div>
      
    <div class="btn-group" role="group" aria-label="Third group">
      <button type="button" class="btn btn-info show-estimates">SHOW ESTIMATES</button>
    </div>
  </div>
</template>

<style scoped>
.custom-input-box {
  position: relative;
  display: inline-flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  min-width: 150px;
  height: 30px;
  padding: 0 0.75rem;
  border-radius: 0.375rem;
  border: 1px solid #cbd5e1;
  background-color: #f1f5f9;
  color: #0f172a;
  cursor: pointer;
  transition: all 0.2s ease;
}

.custom-input-box.active {
  background-color: #e2e8f0;
  border-color: #94a3b8;
}

.label {
  display: block;
  font-size: 0.6rem;
  font-weight: 700;
  text-transform: uppercase;
  color: #334155;
  line-height: 1;
}

.custom-input-box.active .label {
  color: #0f172a;
}


.value-text {
  margin-top: 0.1rem;
  color: #0f172a;
  font-size: 0.7rem;
  font-weight: 600;
  line-height: 1;
}

.btn-toolbar .btn {
  font-size: 0.75rem;
  color: #0f172a;
  height: 30px;
}

.btn-toolbar {
  width: 100%;
  display: flex;
  justify-content: space-around;
  align-items: center;
  gap: 0.5rem;
  flex-wrap: wrap;
}

.grey-btn,
.passenger-input {
  background-color: #e2e8f0;
  color: #0f172a;
  border-color: #cbd5e1;
}

.grey-btn:hover,
.passenger-input:hover {
  background-color: white;
  color: #0f172a;
}

.passenger-input {
  display: inline-flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
  min-width: 100px;
  height: 30px;
  padding: 0.3rem 0.75rem;
}

.passenger-input .label {
  font-size: 0.6rem;
  font-weight: 700;
  text-transform: uppercase;
  color: #334155;
  line-height: 1;
}

.passenger-input .value-text {
  margin-top: 0.1rem;
  font-size: 0.7rem;
  font-weight: 600;
  color: #0f172a;
  line-height: 1;
}

.btn-group .btn.btn-info.show-estimates {
  background-color: transparent;
  border: 1px solid white;
  border-radius: 999px;
  color: white;
}

.btn-group .btn.btn-info.show-estimates:hover {
  background-color: white;
  color: #0f172a;
}

.btn-icon {
  min-width: 38px;
  height: 30px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 0;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(3px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(5px); }
  to { opacity: 1; transform: translateY(0); }
}
</style>