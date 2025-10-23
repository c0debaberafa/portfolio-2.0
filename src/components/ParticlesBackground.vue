<script setup lang="ts">
import { onMounted, onUnmounted } from "vue";

// Declare particlesJS on window object
declare global {
  interface Window {
    particlesJS: (id: string, config: any) => void;
  }
}

onMounted(() => {
  if (typeof window === "undefined") return;

  const script = document.createElement("script");
  script.src = "https://cdn.jsdelivr.net/particles.js/2.0.0/particles.min.js";
  script.onload = () => {
    if (window.particlesJS) {
      // Load particles in main background
      window.particlesJS.load("particles", "/particles.json", () => {
        console.log("Particles loaded successfully");
      });
    }
  };
  script.onerror = () => {
    console.error("Failed to load particles.js");
  };
  document.head.appendChild(script);
});

onUnmounted(() => {
  const existingScript = document.querySelector('script[src*="particles.js"]');
  if (existingScript) {
    existingScript.remove();
  }
});
</script>

<template>
  <div>
    <!-- Background Image -->
    <div
      class="fixed top-0 left-0 w-screen h-screen z-0 pointer-events-none"
      style="
        background-image: url('/dark-bg.jpg');
        background-attachment: fixed;
        background-position: center top;
        background-size: cover;
      "
    />

    <!-- Particles Layer -->
    <div class="fixed top-0 left-0 w-screen h-screen z-10 pointer-events-none">
      <div
        id="particles"
        class="absolute inset-0 w-full h-full opacity-100"
        style="background: transparent"
      />
    </div>
  </div>
</template>
