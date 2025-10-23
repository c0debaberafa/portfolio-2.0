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
  "Technologist",
  "AI Developer",
  "Creative",
  "Eternal Academic",
  "Frontend Developer",
  "Product Designer",
] as const;
const writeups: Record<(typeof wCategories)[number], string> = {
  Technologist:
    "Nice to meet you, I'm Rafa! My work lives at the intersection of design, code, and emotion. From building stories through frontend interfaces, fine-tuning AI companions, to writing scripts that turns hours of work into minutes, I love bringing delight to people through my work. Eternally curious, obsessed with craft, and always open to exciting opportunities.",
  "Frontend Developer":
    "These days I'm most at home with frontend development. From crafting custom JavaScript and CSS projects, I eventually moved into frameworks like React and now find the most joy in the structure and clarity of of Vue 3, Pinia, and TypeScript especiallly when I designed a simulation visualization for local traffic in Manila. ",
  "Product Designer":
    "When it comes to design, I care about form and function equally. Whether building a simulation dashboard or client website, I start with wireframes in Figma to capture the project's essence, then bring it to life through thoughtful interaction and motion. I’m not satisfied until a design both fulfills its purpose and captures attention through immersive detail.",
  "AI Developer":
    "Apart from my usual work, I’m building Fred — an AI journaling companion that grows with you. What began as an AI engineering role as co-founder became a hackathon-winning startup. I’m now fine-tuning its model to better capture emotional continuity and reflection — exploring how AI can deepen our relationship with ourselves.",
  Creative:
    "Beyond code, I've produced content campaigns reaching millions. I've learned the importance of storytelling through video, photo, and copy — a skill that reflects in how I build digital experiences. I love blending narrative, visuals, and strategy to make ideas resonate. ",
  "Eternal Academic":
    "I discovered my hunger for learning in UP Diliman, and it never stopped. I aim to finish at least one book a week, believing the best developers in this age of AI will be those who learn fastest and most deeply. My current reading list spans deep learning, philosophy, Japanese language, and chess.",
};
const selectedWCategory = ref<(typeof wCategories)[number]>("Technologist");
</script>

<template>
  <section
    class="min-h-screen flex justify-center md:justify-end items-end pb-16 px-4"
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
      class="flex flex-col justify-end h-full items-center md:items-start w-full md:max-w-none"
    >
      <div class="flex flex-col items-center">
        <img
          src="/hero.png"
          alt="Rafa Photo"
          class="w-32 h-32 rounded-full border-2 border-black/20"
        />
        <div class="flex gap-4 mt-2">
          <PhEnvelopeSimple
            :size="24"
            class="text-white/40 hover:text-[#fc3113]"
          />
          <PhGithubLogo :size="24" class="text-white/40 hover:text-[#fc3113]" />
          <PhDiscordLogo
            :size="24"
            class="text-white/40 hover:text-[#fc3113]"
          />
          <PhXLogo :size="24" class="text-white/40 hover:text-[#fc3113]" />
        </div>
      </div>
      <h1
        class="text-4xl sm:text-6xl md:text-8xl lg:text-[120px] text-center lg:text-left text-white mix-blend-difference"
        :style="{ fontFamily: 'Akira' }"
      >
        Rafa
      </h1>
      <h1
        class="text-4xl sm:text-6xl md:text-8xl lg:text-[120px] text-center lg:text-left text-white mix-blend-difference"
        :style="{ fontFamily: 'Akira' }"
      >
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
        class="bg-black/80 backdrop-blur-md hover:backdrop-blur-lg border border-[#fc3113]/80 rounded-xl shadow-lg px-4 py-3 transition duration-8000 ease-in-out mt-4 w-full min-h-32"
      >
        <div class="text-left" :style="{ fontFamily: 'JetBrains Mono' }">
          {{ writeups[selectedWCategory] }}
        </div>
      </div>
    </div>
  </section>
</template>
