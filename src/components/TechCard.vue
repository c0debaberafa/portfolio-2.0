<template>
  <div
    class="flex flex-col items-center justify-center w-16 sm:w-24 h-16 md:w-32 sm:h-24 md:h-32 p-2 bg-black/80 backdrop-blur-md border rounded-xl border-[#fc3113] shadow-lg transition-all duration-200 cursor-pointer group"
  >
    <!-- Render the icon component -->
    <component
      v-if="state.icon"
      :is="state.icon"
      class="w-8 h-8 mb-2 group-hover:scale-110 transition-transform duration-200"
      :style="{ color: state.color }"
    />
    <!-- Or render an image source (e.g., SVG in public/techstack) -->
    <img
      v-else-if="state.imgSrc"
      :src="state.imgSrc"
      alt=""
      class="w-12 md:w-16 h-12 md:h-16 object-contain group-hover:scale-110 transition-transform duration-200"
      draggable="false"
    />
    <p
      class="text-xs hidden md:block mt-2 text-white/40 text-center group-hover:text-[#fc3113] transition-colors duration-200"
      :style="{ fontFamily: state.font }"
    >
      {{ state.name }}
    </p>
  </div>
</template>

<script setup lang="ts">
import type { Component } from "vue";

const props = defineProps<{
  icon?: Component;
  name: string;
  color?: string;
  font?: string;
  imgSrc?: string;
}>();

const state = props;
</script>
