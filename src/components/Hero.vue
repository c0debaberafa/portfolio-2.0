<script setup lang="ts">
import { computed, ref } from "vue";
import Card from "./Card.vue";

import {
  PhDiscordLogo,
  PhEnvelopeSimple,
  PhGithubLogo,
  PhXLogo,
  PhFacebookLogo,
  PhInstagramLogo,
  PhSpotifyLogo,
} from "@phosphor-icons/vue";

const state = {
  customFont: "JetBrains Mono",
} as const;

// Writeup state (kept separate from tech filters)
const wCategories = [
  "Intro",
  "Eternal Academic",
  "Frontend Developer",
  "AI Developer",
  "Product Designer",
  "Creative",
] as const;
const writeups: Record<(typeof wCategories)[number], string> = {
  Intro:
    "Nice to meet you, I'm Rafa! My work lives at the intersection of design, code, and communication. From building narratives through web interfaces, to developing AI companions and writing scripts that turn hours of work into minutes, I find great fulfillment in bringing delight to people through my work. Eternally curious, constantly playing with new tech, and always searching for exciting opportunities.",
  "Frontend Developer":
    "These days I'm most at home with frontend development. I began with custom JavaScript and CSS projects, then eventually moved into frameworks like React and Vue. From government projects to private clients to startups, I have a broad range of experiences across different industries, and I'm always working to bring that unique perspective to whatever I'm working on.",
  "Product Designer":
    "When it comes to design, I care about form and function equally. When I'm designing a new product, I generally start with wireframes in Figma or sketches in my notebook to capture the project's essence. I’m not satisfied until a design both fulfills its function and captures attention through elegant design. My designs can be somewhat opinionated, but I've learned to iterate quickly.",
  "AI Developer":
    "Apart from usual work, I primarily work with AI these days: both API tooling and actual LLM / ML models. I truly this new technology fascinating, and I'm always exploring how AI can deepen our relationship with ourselves. Apart from starting as an AI Engineer and Co-Founder for Fred (my first hackathon-winning startup), I'm now working as sole Founder of Constellate and am now progressing toward a deeper understanding of models and math.",
  Creative:
    "Beyond code, I've produced content campaigns reaching millions. I've learned to foster my aptitude for storytelling through video, photo, and copy — a skill that reflects in how I build digital experiences. I love blending narrative, visuals, and strategy to make messages resonate. I truly believe the best products win in the end because of their emotional pull on the user, apart from fulfilling function.",
  "Eternal Academic":
    "I've been programming since high school, but discovered my true penchant for learning in the University of the Philippines studying Computer Science. I aim to finish at least one book a week, believing the best developers in this age of AI will be those who learn fastest and most deeply. My current reading list spans deep learning, philosophy, Japanese language, and fiction (Dune is my current favorite).",
};
const selectedWCategory = ref<(typeof wCategories)[number]>("Intro");
</script>

<template>
  <section
    class="scroll-mt-20 min-h-screen flex justify-center md:justify-end items-end pb-8 md:pb-16 px-4"
  >
    <!-- <p
      class="absolute top-20 right-8 text-right text-sm text-white/40 mix-blend-difference z-10"
      :style="{ fontFamily: 'Jetbrains Mono' }"
    >
      <b
        >Exploring how technology can create delightful, human-centered
        experiences.</b
      >
    </p> -->
    <div
      class="flex flex-col justify-end h-full items-center lg:items-start w-full md:max-w-none"
    >
      <div class="flex flex-col items-center">
        <img
          src="/hero.png"
          alt="Rafa Photo"
          class="w-32 h-32 rounded-full border-2 border-black/20"
        />
        <div class="flex gap-2 sm:gap-4 mt-2">
          <a
            href="mailto:rafa@tora.media"
            target="_blank"
            rel="noopener noreferrer"
            class="cursor-pointer"
          >
            <PhEnvelopeSimple
              :size="24"
              class="text-white/40 hover:text-[#fc3113]"
            />
          </a>
          <a
            href="https://github.com/c0debaberafa"
            target="_blank"
            rel="noopener noreferrer"
            class="cursor-pointer"
          >
            <PhGithubLogo
              :size="24"
              class="text-white/40 hover:text-[#fc3113]"
            />
          </a>
          <a
            href="https://discord.com/users/rivermouth"
            target="_blank"
            rel="noopener noreferrer"
            class="cursor-pointer"
          >
            <PhDiscordLogo
              :size="24"
              class="text-white/40 hover:text-[#fc3113]"
            />
          </a>
          <a
            href="https://x.com/toramatsu__"
            target="_blank"
            rel="noopener noreferrer"
            class="cursor-pointer"
          >
            <PhXLogo :size="24" class="text-white/40 hover:text-[#fc3113]" />
          </a>
        </div>
      </div>
      <h1
        class="text-4xl sm:text-6xl md:text-8xl lg:text-[120px] text-center lg:text-left text-white mix-blend-difference text-shadow-xl text-shadow-white"
        :style="{ fontFamily: 'Akira' }"
      >
        Rafa
        <br />
        Partosa
      </h1>
      <div class="w-full h-px border-[#fc3113] bg-[#fc3113]/80 mb-4"></div>
      <div class="grid w-full gap-2 grid-cols-1 sm:grid-cols-3 lg:grid-cols-6">
        <button
          v-for="cat in wCategories"
          :key="cat"
          @click="selectedWCategory = cat"
          class="font-mono font-bold text-xs backdrop-blur-md hover:backdrop-blur-lg border rounded-full px-3 py-1 whitespace-nowrap transition-all duration-300"
          :class="{
            'text-white border-white': selectedWCategory === cat,
            'text-[#fc3113] bg-black/80 border-[#fc3113] hover:bg-black/20 hover:border-white hover:text-white':
              selectedWCategory !== cat,
          }"
          :style="{ fontFamily: 'JetBrains Mono' }"
        >
          {{ cat }}
        </button>
      </div>
      <div
        class="bg-black/90 backdrop-blur-lg border border-[#fc3113]/80 rounded-xl shadow-lg px-4 py-3 transition duration-8000 ease-in-out mt-4 w-full min-h-32"
      >
        <div
          class="text-left text-sm md:text-md"
          :style="{ fontFamily: 'JetBrains Mono' }"
        >
          {{ writeups[selectedWCategory] }}
        </div>
      </div>
    </div>
  </section>
</template>
