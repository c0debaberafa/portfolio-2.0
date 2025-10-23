<script setup lang="ts">
defineProps<{ customClass?: string }>();
</script>

<template>
  <div
    :class="[
      'bg-black/70 hover:bg-black/80 backdrop-blur-md hover:backdrop-blur-lg border-2 border-black/20 rounded-xl shadow-lg p-6 transition duration-8000 ease-in-out ',
      customClass,
    ]"
  >
    <slot />
  </div>
</template>
