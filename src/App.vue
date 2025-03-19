<template>
  <div class="app">
    <!-- Beverage Mug and Animation -->
    <div class="mug-container">
      <Beverage 
        :isIced="currentTemp === 'Cold'" 
        :base="selectedBase" 
        :creamer="selectedCreamer" 
        :syrup="selectedSyrup" 
      />
    </div>

    <!-- Options for customization -->
    <div class="options-container">
      <div class="option">
        <label>Temperature:</label>
        <button 
          v-for="temp in temps" 
          :key="temp"
          :class="{ active: currentTemp === temp }"
          @click="currentTemp = temp">
          {{ temp }}
        </button>
      </div>

      <div class="option">
        <label>Creamer:</label>
        <button 
          v-for="creamer in creamers" 
          :key="creamer.id"
          :class="{ active: selectedCreamer.id === creamer.id }"
          @click="selectedCreamer = creamer">
          {{ creamer.name }}
        </button>
      </div>

      <div class="option">
        <label>Syrup:</label>
        <button 
          v-for="syrup in syrups" 
          :key="syrup.id"
          :class="{ active: selectedSyrup.id === syrup.id }"
          @click="selectedSyrup = syrup">
          {{ syrup.name }}
        </button>
      </div>

      <div class="option">
        <label>Base Beverage:</label>
        <button 
          v-for="base in bases" 
          :key="base.id"
          :class="{ active: selectedBase.id === base.id }"
          @click="selectedBase = base">
          {{ base.name }}
        </button>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import Beverage from "./components/Beverage.vue";
import { temps, bases, creamers, syrups } from "./stores/beverage";

// Reactive data for selections
const currentTemp = ref(temps.value[1]); // Default: "Cold"
const selectedBase = ref(bases.value[0]); // Default: "Black Tea"
const selectedCreamer = ref(creamers.value[0]); // Default: "No Cream"
const selectedSyrup = ref(syrups.value[0]); // Default: "No Syrup"
</script>

<style scoped>
/* Brown gradient background covering the whole viewport */
body,
html {
  height: 100%;
  margin: 0;
  background-color: #6e4228; /* Solid brown */
  background: linear-gradient(to bottom, #6e4228 0%, #956f5a 100%); /* Gradient */
  display: flex;
  justify-content: center;
  align-items: center;
}

/* App wrapper centers everything */
.app {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  min-height: 100vh; /* Ensures it covers the whole screen */
}

/* Beverage Mug positioning */
.mug-container {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 40px; /* Space between mug and options */
  height: 50%; /* Adjust height to fit animations */
}

/* Options layout */
.options-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 20px;
}

.option {
  margin-bottom: 15px;
}

button {
  background-color: #f5f5f5;
  border: 2px solid #aaa;
  padding: 10px;
  margin: 5px;
  cursor: pointer;
  border-radius: 5px;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #d3d3d3;
}

button.active {
  background-color: #007bff;
  color: white;
}

button:focus {
  outline: none;
}
</style>
