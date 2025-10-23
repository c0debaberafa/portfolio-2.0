<script setup lang="ts">
import { defineSlots } from "vue";

defineSlots<{
  default(): any;
}>();
</script>

<template>
  <div class="relative">
    <!-- Full width dark frosted glass background -->
    <div
      class="absolute inset-y-0 bg-black/60 backdrop-blur-lg z-20 border-2"
      style="left: calc(-50vw + 50%); right: calc(-50vw + 50%)"
    ></div>

    <!-- Content with original margins preserved -->
    <div class="relative z-30">
      <slot />
    </div>
  </div>
</template>
