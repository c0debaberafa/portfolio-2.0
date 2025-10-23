<script setup lang="ts">
import Navbar from "./components/Navbar.vue";
import Hero from "./components/Hero.vue";
import TechStack from "./components/TechStack.vue";
import Projects from "./components/Projects.vue";
import Experience from "./components/Experience.vue";
import ParticlesBackground from "./components/ParticlesBackground.vue";
import GlassSection from "./components/GlassSection.vue";
import Education from "./components/Education.vue";
import Afk from "./components/Afk.vue";
import Footer from "./components/Footer.vue";
</script>

<template>
  <div class="relative">
    <ParticlesBackground />
    <Navbar />
    <div class="container mx-auto px-8 md:px-16 relative z-30 gap-16">
      <Hero id="about" />
      <GlassSection>
        <TechStack />
        <Projects id="projects" />
        <Experience id="experience" />
        <Education />
      </GlassSection>
      <div class="flex items-center justify-center">
        <Afk />
      </div>
    </div>
  </div>
  <Footer />
</template>
