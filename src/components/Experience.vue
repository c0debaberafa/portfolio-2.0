<template>
  <section class="min-h-screen py-12">
    <div class="w-full px-4">
      <div class="w-full">
        <!-- Header -->
        <h1
          class="text-4xl md:text-6xl text-left text-[#fc3113] mix-blend-difference mb-4"
          :style="{ fontFamily: 'Akira' }"
        >
          Experience
        </h1>
        <div class="w-full h-px border-[#fc3113] bg-[#fc3113]/80 mb-12"></div>

        <!-- Experience Items -->
        <div class="space-y-8">
          <div
            v-for="(exp, index) in experiences"
            :key="exp.id"
            class="group relative"
          >
            <!-- Dot and Timestamp Row -->
            <div
              class="flex items-center gap-4 mb-4 md:justify-start justify-center"
            >
              <!-- Timeline Dot -->
              <div
                class="hidden md:block w-4 h-4 rounded-full bg-[#fc3113] flex-shrink-0"
              ></div>

              <!-- Time Badge -->
              <span
                class="bg-[#fc3113] text-black border border-[#fc3113]/30 px-3 py-1 rounded-full text-xs font-mono font-bold"
                style="font-family: 'JetBrains Mono', monospace"
              >
                {{ exp.time }}
              </span>
            </div>

            <!-- Experience Card -->
            <div
              :ref="(el) => (cardRefs[index] = el)"
              class="md:ml-8 ml-0 bg-black/80 backdrop-blur-lg border border-[#fc3113]/80 rounded-xl shadow-lg group/card relative p-8"
            >
              <div
                class="flex flex-col md:flex-row md:items-start items-center gap-6"
              >
                <!-- Company Logo -->
                <div class="flex-shrink-0">
                  <img
                    :src="exp.logo"
                    :alt="`${exp.company} logo`"
                    class="h-16 w-16 object-contain"
                  />
                </div>

                <!-- Content -->
                <div class="flex-grow min-w-0 md:text-left text-center">
                  <!-- Header with Company, Title, and Time -->
                  <div class="mb-4">
                    <div class="md:text-left text-center">
                      <h3
                        v-if="companyLinks[exp.company]"
                        class="md:text-left text-center text-2xl font-bold text-white flex items-center gap-1 md:justify-start justify-center"
                      >
                        <a
                          :href="companyLinks[exp.company]"
                          target="_blank"
                          rel="noopener noreferrer"
                          class="hover:text-[#fc3113] text-white font-bold transition-colors"
                          @click.stop
                        >
                          {{ exp.company }}
                        </a>
                        <PhLinkSimple :size="16" class="text-[#fc3113]" />
                      </h3>
                      <h3
                        v-else
                        class="md:text-left text-center text-2xl font-bold text-white"
                      >
                        {{ exp.company }}
                      </h3>
                      <span
                        class="block md:text-left text-center text-xl text-[#fc3113] font-bold"
                      >
                        {{ exp.title }}
                      </span>
                    </div>
                  </div>
                  <!-- Skills -->
                  <div
                    class="flex flex-wrap gap-2 mb-4 md:justify-start justify-center"
                  >
                    <span
                      v-for="(skill, idx) in exp.skills"
                      :key="idx"
                      class="bg-[#fc3113]/20 text-[#fc3113] border border-[#fc3113]/30 px-3 py-1 rounded-full text-xs font-mono font-normal"
                      style="font-family: 'JetBrains Mono', monospace"
                    >
                      {{ skill }}
                    </span>
                  </div>
                  <!-- Description -->
                  <div class="max-h-96 opacity-100 translate-y-0">
                    <div class="text-left pt-2 border-t border-[#fc3113]">
                      <ul class="list-none">
                        <li
                          v-for="(sentence, idx) in formatDescription(
                            exp.description
                          )"
                          :key="idx"
                          class="flex items-start gap-2 mb-1"
                        >
                          <span
                            class="text-white/60 font-mono text-sm mt-1 flex-shrink-0"
                            >•</span
                          >
                          <span
                            class="text-white/80 leading-relaxed font-mono"
                            style="font-family: 'JetBrains Mono', monospace"
                            v-html="sentence"
                          />
                        </li>
                      </ul>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, computed, onMounted, nextTick } from "vue";
import { PhLinkSimple } from "@phosphor-icons/vue";
// Types
interface Experience {
  id: string;
  company: string;
  logo: string;
  title: string;
  description: string;
  time: string;
  skills: string[];
}

interface ToraClient {
  id: string;
  name: string;
  logo: string;
  url: string;
  instagram: string;
}

// Reactive state
const cardRefs = ref<(HTMLElement | null)[]>([]);

// Tora Media clients data
const toraClients: ToraClient[] = [
  {
    id: "1",
    name: "uCycle",
    logo: "/ucycle.jpg",
    url: "https://www.ucycle.life/",
    instagram: "https://www.instagram.com/ucycle.life/",
  },
  {
    id: "2",
    name: "CoFitness",
    logo: "/cofit.png",
    url: "https://www.cofitness.com.ph/",
    instagram: "https://www.instagram.com/cofitnessph/",
  },
  {
    id: "3",
    name: "Ultraboxx",
    logo: "/ultraboxx.png",
    url: "https://ultraboxx.ph/",
    instagram: "https://www.instagram.com/ultra.boxx/",
  },
];

// Experience data
const experiences: Experience[] = [
  {
    id: "1",
    company: "Tora Media",
    logo: "/tora-white.png",
    title: "Frontend, Creative Lead",
    time: "06.2023 - 06.2025",
    description:
      "Rebuilt lightweight frontend systems powering <span class='text-[#fc3113]'>2,000+ monthly client interactions</span>. Designed scalable content systems clients could independently manage. Directed creative production for digital assets, generating <span class='text-[#fc3113]'>1.5M+ views</span>.",
    skills: ["JavaScript", "HTML", "CSS", "Adobe Suite", "Figma"],
  },
  {
    id: "2",
    company: "TechnologyAdvice",
    logo: "/ta-logo.jpeg",
    title: "Research Associate",
    time: "10.2022 - 01.2024",
    description:
      "Designed and optimized reusable frontend components for high-traffic pages. Conducted competitive SEO research and development, improving rankings for competitive keywords by an accumulated <span class='text-[#fc3113]'>600%</span>. Contributed to an estimated <span class='text-[#fc3113]'>22-30% uplift in user engagement</span>.",
    skills: ["JavaScript", "HTML", "CSS", "SEO"],
  },
  {
    id: "3",
    company: "Presidential Communications Office",
    logo: "/pco-logo.png",
    title: "Admin Assistant I",
    time: "04.2021 - 04.2022",
    description:
      "Coordinated and deployed official government websites, reaching <span class='text-[#fc3113]'>12M+ page views</span>. Led a small team in producing official multimedia content for nationwide engagement.",
    skills: ["JavaScript", "HTML", "CSS", "Adobe Suite"],
  },
];

// Company links
const companyLinks: { [key: string]: string } = {
  TechnologyAdvice: "https://technologyadvice.com/",
  "Presidential Communications Office": "https://pco.gov.ph/",
};

// Methods
const formatDescription = (description: string): string[] => {
  const sentences = description
    .split(/\.\s|\.$/)
    .filter((s) => s.trim().length > 0);
  return sentences.map((sentence) => sentence.trim() + ".");
};

// Initialize card refs
onMounted(() => {
  cardRefs.value = new Array(experiences.length).fill(null);
});
</script>
