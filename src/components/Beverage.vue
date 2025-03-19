<template>
  <Mug>
    <Cold v-if="isIced" />
    <Hot v-else />
    <Contents>
      <template v-slot:top>
        <!-- Render creamer only if it's selected -->
        <Creamer v-if="creamer.id !== 'c1'" :color="creamer.color" :name="creamer.name" />
      </template>
      <template v-slot:mid>
        <!-- Render syrup only if it's selected -->
        <Syrup v-if="syrup.id !== 's1'" :color="syrup.color" :name="syrup.name" />
      </template>
      <template v-slot:bottom>
        <!-- Render the base beverage -->
        <Base :color="base.color" :name="base.name" />
      </template>
    </Contents>
  </Mug>
</template>

<script setup lang="ts">
import Contents from "./Contents.vue";
import Mug from "./Mug.vue";
import Syrup from "./Syrup.vue";
import Base from "./Base.vue";
import Creamer from "./Creamer.vue";
import Hot from "./Hot.vue";
import Cold from "./Cold.vue";

import { bases, creamers, syrups } from "../stores/beverage";

type Props = {
  isIced: boolean;
  base: typeof bases[]; // Base item
  creamer: typeof creamers[]; // Creamer item
  syrup: typeof syrups[]; // Syrup item
};

defineProps<Props>();
</script>
