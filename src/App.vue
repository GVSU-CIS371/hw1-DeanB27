<template>
  <div>
    <Beverage
      :isIced="currentTemp === 'Cold'"
      :creamer="currentCreamer"
      :syrup="currentSyrup"
      :base="currentBase"
    />
    
    <ul>
      <li>
        <template v-for="temp in temps" :key="temp">
          <label>
            <input
              type="radio"
              name="temperature"
              :id="`r${temp}`"
              :value="temp"
              v-model="currentTemp"
            />
            {{ temp }}
          </label>
        </template>
      </li>
    </ul>

    <ul>
      <li>
        <label for="creamer">Creamer:</label>
        <select v-model="currentCreamer" id="creamer">
          <option v-for="creamer in creamers" :key="creamer.id" :value="creamer">
            {{ creamer.name }}
          </option>
        </select>
      </li>
      <li>
        <label for="syrup">Syrup:</label>
        <select v-model="currentSyrup" id="syrup">
          <option v-for="syrup in syrups" :key="syrup.id" :value="syrup">
            {{ syrup.name }}
          </option>
        </select>
      </li>
      <li>
        <label for="base">Base Beverage:</label>
        <select v-model="currentBase" id="base">
          <option v-for="base in bases" :key="base.id" :value="base">
            {{ base.name }}
          </option>
        </select>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import Beverage from "./components/Beverage.vue";
import { temps, currentTemp, bases, currentBase, creamers, currentCreamer, syrups, currentSyrup } from "./stores/beverage";
</script>

<style lang="scss">
body,
html {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  background-color: #6e4228;
  background: linear-gradient(to bottom, #6e4228 0%, #956f5a 100%);
}
ul {
  list-style: none;
}
</style>
