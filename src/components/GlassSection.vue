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
      class="absolute inset-y-0 bg-black/100 z-20 border-t border-b border-[#fc3113]"
      style="left: calc(-50vw + 50%); right: calc(-50vw + 50%)"
    ></div>

    <!-- Content with original margins preserved -->
    <div class="relative z-30 py-8 md:py-16 space-y-8 md:space-y-16">
      <slot />
    </div>
  </div>
</template>
