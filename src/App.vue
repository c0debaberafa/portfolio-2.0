<script setup lang="ts">
import Navbar from "./components/Navbar.vue";
import Hero from "./components/Hero.vue";
import TechStack from "./components/TechStack.vue";
import Projects from "./components/Projects.vue";
import Experience from "./components/Experience.vue";
import ParticlesBackground from "./components/ParticlesBackground.vue";
import GlassSection from "./components/GlassSection.vue";
</script>

<template>
  <div class="relative">
    <ParticlesBackground />
    <Navbar />
    <div class="container mx-auto px-4 md:px-8 relative z-30">
      <Hero id="about" />
      <GlassSection>
        <TechStack />
        <Projects id="projects" />
        <Experience id="experience" />
      </GlassSection>
    </div>
  </div>
</template>
