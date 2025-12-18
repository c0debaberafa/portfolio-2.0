<script setup lang="ts">
import { ref, onMounted, onUnmounted } from "vue";

const scrolled = ref(false);

const handleScroll = () => {
  scrolled.value = window.scrollY > 20;
};

onMounted(() => window.addEventListener("scroll", handleScroll));
onUnmounted(() => window.removeEventListener("scroll", handleScroll));
</script>

<template>
  <nav
    :class="[
      'fixed top-0 left-0 w-full z-50 transition-all duration-300',
      scrolled
        ? 'bg-black/50 backdrop-blur-lg border-b border-[#fc3113]/40'
        : ' border-white/10',
    ]"
  >
    <div
      class="max-w-7xl mx-auto px-4 md:px-8 h-16 flex items-center justify-between"
    >
      <!-- Logo / Name -->
      <div class="flex items-center gap-2">
        <img src="/tora-orange.png" alt="Logo" class="w-8 h-8" />
      </div>

      <!-- Nav Links -->
      <div class="hidden md:flex items-center gap-6">
        <a
          href="#about"
          class="text-white/80 hover:text-[#fc3113] transition-colors duration-200 flex items-center"
          :style="{ fontFamily: 'JetBrains Mono' }"
        >
          About
        </a>
        <a
          href="#projects"
          class="text-white/80 hover:text-[#fc3113] transition-colors duration-200 flex items-center"
          :style="{ fontFamily: 'JetBrains Mono' }"
        >
          Projects
        </a>
        <a
          href="#experience"
          class="text-white/80 hover:text-[#fc3113] transition-colors duration-200 flex items-center"
          :style="{ fontFamily: 'JetBrains Mono' }"
        >
          Experience
        </a>
        <a
          href="/resume.pdf"
          download
          class="text-white/80 hover:text-[#fc3113] transition-colors duration-200 border border-white/20 hover:border-[#fc3113] px-4 py-2 rounded-full flex items-center"
          :style="{ fontFamily: 'JetBrains Mono' }"
        >
          Download Resume
        </a>
      </div>

      <!-- Mobile Menu (optional for later) -->
      <div class="md:hidden">
        <button class="text-white hover:text-[#fc3113]">☰</button>
      </div>
    </div>
  </nav>
</template>
