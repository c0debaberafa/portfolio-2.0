<script setup lang="ts">
import { ref } from "vue";
import { PhX } from "@phosphor-icons/vue";

interface Project {
  id: string;
  title: string;
  time: string;
  preview: string;
  githubUrl: string;
  demoUrl?: string;
  subheader: string;
  description: string;
  skills: string[];
}

// Modal state
const selectedProject = ref<Project | null>(null);
const isModalOpen = ref(false);

const openModal = (project: Project) => {
  selectedProject.value = project;
  isModalOpen.value = true;
};

const closeModal = () => {
  isModalOpen.value = false;
  selectedProject.value = null;
};

const projects = ref<Project[]>([
  {
    id: "0",
    title: "Trike Sim Dashboard",
    time: "Jun 2025",
    preview: "/trike-sim.png",
    githubUrl: "https://github.com/c0debaberafa/trike-sim-dashboard-demo",
    demoUrl: "https://trike-sim-dashboard-demo.vercel.app/",
    subheader:
      "Your voice-first AI companion for intentional self-reflection and life engineering.",
    description:
      "As an extension of my project with the National Commission on Transport Studies, I developed a responsive trike simulation dashboard to allow for frame-by-frame analysis of simulation data. Built with a modular Vue 3 + Pinia architecture, the dashboard integrates dynamic event logs, passenger/tricycle status tracking, and parameter tuning through reactive state management, enabling researchers to visualize transport dynamics and optimize fleet configurations.",
    skills: ["Vue 3", "TypeScript", "Nuxt.js", "Pinia", "Playwright", "Vite"],
  },
  {
    id: "1",
    title: "Fred AI",
    time: "Jun 2025",
    preview: "/fred.png",
    githubUrl: "https://github.com/c0debaberafa/mirror",
    demoUrl: "https://fredai.xyz",
    subheader:
      "Your voice-first AI companion for intentional self-reflection and life engineering.",
    description:
      "An AI-powered journaling app for engineering your life that turns your voice entries into personal insights. Designed for founders to supercharge productivity. Built with TypeScript, React, and OpenAI and Vapi integrations, Fred detects emotional patterns, tracks growth, and helps users reflect with intention. Winner of Stanford-affiliated ASES Manila’s “0 to 1” hackathon.",
    skills: [
      "Next.js",
      "React",
      "Tailwind CSS",
      "shadcn/ui",
      "TypeScript",
      "Supabase",
      "Drizzle ORM",
      "VAPI.ai",
      "Vercel",
    ],
  },
  {
    id: "2",
    title: "Traffic Modeling Simulation",
    time: "May 2025",
    preview: "/trike.png",
    githubUrl: "https://github.com/c0debaberafa/tricycle-simulation",
    subheader:
      "A traffic simulation tool that visualizes tricycle movement in Manila to support urban planning and local transport policy.",
    description:
      "Here I led both simulation and front-end development of an agent-based system modeling tricycle productivity, terminal usage, and passenger wait times. Built in collaboration with the National Commission on Transport Services, the project aimed to improve their national traffic simulator by introducing localized dynamics for small-scale public vehicles.",
    skills: ["Python", "JavaScript", "NumPy", "Leaflet", "Data Visualization"],
  },
  {
    id: "3",
    title: "DevOS",
    time: "May 2025",
    preview: "/devos.png",
    githubUrl:
      "https://github.com/c0debaberafa/devos-decentralized-voting?tab=readme-ov-file",
    demoUrl: "https://devos-app.vercel.app/",
    subheader:
      "A traffic simulation tool that visualizes tricycle movement in Manila to support urban planning and local transport policy.",
    description:
      "Designed as a transparent, permissioned voting system built on blockchain principles. Enabled secure, tamper-resistant election workflows by combining a web frontend, backend APIs and smart contract components. Key features include user role management, vote recording, encrypted ballot handling and real-time results data. Technologies used: Solidity (smart contracts), Web3/Ethereum or EVM-compatible chain, Node.js backend, React (or equivalent) UI, and REST APIs for orchestration.",
    skills: ["Solidity", "Ethereum", "Rust", "Node.js", "React"],
  },
  {
    id: "4",
    title: "PubTracker",
    time: "May 2025",
    preview: "/pubtracker.png",
    githubUrl: "https://github.com/c0debaberafa/pubtrackerbot",
    subheader:
      "A traffic simulation tool that visualizes tricycle movement in Manila to support urban planning and local transport policy.",
    description:
      "A simple but effective script that I wrote to scrape Facebook publicity metrics, effectively reducing months of work into minutes of script runtime. Produced on behalf of the Engineering Student Council, and awarded Breakthrough Project of the Year. I believe they're still using it today.",
    skills: ["Python", "BeautifulSoup", "Selenium", "Chromium"],
  },
]);
</script>

<template>
  <section class="scroll-mt-20 relative flex flex-col h-full justify-center">
    <!-- Title -->
    <h1
      class="text-4xl sm:text-6xl text-center md:text-left text-[#fc3113] mix-blend-difference"
      :style="{ fontFamily: 'Akira' }"
    >
      PROJECTS
    </h1>
    <div class="w-full h-px border-[#fc3113] bg-[#fc3113]/80 mb-4"></div>
    <!-- Projects - Desktop: Horizontal scroll -->
    <!-- Full width scrollable container -->
    <div
      class="hidden lg:flex gap-6 overflow-x-auto"
      style="
        scrollbar-width: none;
        -ms-overflow-style: none;
        margin-left: calc(-50vw + 50%);
        margin-right: calc(-50vw + 50%);
        padding-left: calc(50vw - 50%);
        padding-right: calc(50vw - 50%);
      "
    >
      <div
        v-for="project in projects"
        :key="project.id"
        class="flex-shrink-0 w-[32rem] bg-black/80 backdrop-blur-md border rounded-xl p-6 border-[#fc3113] transition-all duration-200 group"
      >
        <!-- Project preview -->
        <div class="relative overflow-hidden bg-black/20 rounded-lg mb-4">
          <div class="aspect-video relative">
            <img
              :src="project.preview"
              :alt="`${project.title} preview`"
              class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-300"
            />
          </div>
        </div>

        <!-- Project info -->
        <div class="flex flex-col gap-4 text-left">
          <!-- Title + GitHub link + Demo link (if available) -->
          <div class="flex items-center justify-between gap-3 w-full">
            <h3
              class="text-xl font-bold text-white whitespace-nowrap overflow-hidden text-ellipsis pr-4"
            >
              {{ project.title }}
            </h3>
            <div class="flex items-center gap-2 flex-shrink-0">
              <a
                :href="project.githubUrl"
                target="_blank"
                rel="noopener noreferrer"
                class="w-8 h-8 bg-[#fc3113] text-white rounded-full flex items-center justify-center hover:scale-110 transition-transform duration-200"
                aria-label="View on GitHub"
              >
                <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24">
                  <path
                    d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"
                  />
                </svg>
              </a>
              <a
                v-if="project.demoUrl"
                :href="project.demoUrl"
                target="_blank"
                rel="noopener noreferrer"
                class="w-8 h-8 bg-[#fc3113] text-white rounded-full flex items-center justify-center hover:scale-110 transition-transform duration-200"
                aria-label="View live demo"
              >
                <svg
                  class="w-4 h-4"
                  viewBox="0 0 24 24"
                  fill="currentColor"
                  aria-hidden="true"
                >
                  <path d="M8 5v14l11-7z" />
                </svg>
              </a>
            </div>
          </div>

          <!-- Skills under title -->
          <div class="flex flex-wrap gap-2">
            <span
              v-for="skill in project.skills"
              :key="skill"
              class="bg-[#fc3113]/20 text-[#fc3113] border border-[#fc3113]/30 px-2 py-1 rounded-full text-xs"
              :style="{ fontFamily: 'JetBrains Mono' }"
            >
              {{ skill }}
            </span>
          </div>

          <!-- Divider -->
          <div class="border-t border-[#fc3113]/40"></div>

          <!-- Writeup -->
          <p
            class="text-xs text-white leading-relaxed"
            :style="{ fontFamily: 'JetBrains Mono' }"
          >
            {{ project.description }}
          </p>
        </div>
      </div>
    </div>

    <!-- Projects - Medium screens: Column layout with full cards -->
    <div class="hidden sm:block lg:hidden space-y-6">
      <div
        v-for="project in projects"
        :key="project.id"
        class="bg-black/80 backdrop-blur-md border rounded-xl p-4 border-[#fc3113] transition-all duration-200 group"
      >
        <!-- Project preview -->
        <div class="relative overflow-hidden bg-black/20 rounded-lg mb-4">
          <div class="aspect-video relative">
            <img
              :src="project.preview"
              :alt="`${project.title} preview`"
              class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-300"
            />
          </div>
        </div>

        <!-- Project info -->
        <div class="flex flex-col gap-3 text-left">
          <!-- Title + GitHub link + Demo link (if available) -->
          <div class="flex items-center justify-between gap-3 w-full">
            <h3 class="text-lg font-bold text-white">
              {{ project.title }}
            </h3>
            <div class="flex items-center gap-2 flex-shrink-0">
              <a
                :href="project.githubUrl"
                target="_blank"
                rel="noopener noreferrer"
                class="w-7 h-7 bg-[#fc3113] text-white rounded-full flex items-center justify-center hover:scale-110 transition-transform duration-200"
                aria-label="View on GitHub"
              >
                <svg class="w-3 h-3" fill="currentColor" viewBox="0 0 24 24">
                  <path
                    d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"
                  />
                </svg>
              </a>
              <a
                v-if="project.demoUrl"
                :href="project.demoUrl"
                target="_blank"
                rel="noopener noreferrer"
                class="w-7 h-7 bg-[#fc3113] text-white rounded-full flex items-center justify-center hover:scale-110 transition-transform duration-200"
                aria-label="View live demo"
              >
                <svg
                  class="w-3 h-3"
                  viewBox="0 0 24 24"
                  fill="currentColor"
                  aria-hidden="true"
                >
                  <path d="M8 5v14l11-7z" />
                </svg>
              </a>
            </div>
          </div>

          <!-- Skills under title -->
          <div class="flex flex-wrap gap-1">
            <span
              v-for="skill in project.skills"
              :key="skill"
              class="bg-[#fc3113]/20 text-[#fc3113] border border-[#fc3113]/30 px-2 py-0.5 rounded-full text-xs"
              :style="{ fontFamily: 'JetBrains Mono' }"
            >
              {{ skill }}
            </span>
          </div>

          <!-- Divider -->
          <div class="border-t border-[#fc3113]/40"></div>

          <!-- Writeup -->
          <p
            class="text-xs text-white/60 leading-relaxed"
            :style="{ fontFamily: 'JetBrains Mono' }"
          >
            {{ project.description }}
          </p>
        </div>
      </div>
    </div>

    <!-- Projects - Small screens: Compact cards without writeup -->
    <div class="block sm:hidden space-y-4">
      <div
        v-for="project in projects"
        :key="project.id"
        @click="openModal(project)"
        class="bg-black/80 backdrop-blur-md border rounded-lg p-3 border-[#fc3113] transition-all duration-200 group cursor-pointer hover:border-white/50"
      >
        <!-- Project preview -->
        <div class="relative overflow-hidden bg-black/20 rounded-lg mb-3">
          <div class="aspect-video relative">
            <img
              :src="project.preview"
              :alt="`${project.title} preview`"
              class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-300"
            />
          </div>
        </div>

        <!-- Project info -->
        <div class="flex flex-col gap-2 text-left">
          <!-- Title + GitHub link + Demo link (if available) -->
          <div class="flex items-center justify-between gap-2 w-full">
            <h3 class="text-sm font-bold text-white">
              {{ project.title }}
            </h3>
            <div class="flex items-center gap-1 flex-shrink-0">
              <a
                :href="project.githubUrl"
                target="_blank"
                rel="noopener noreferrer"
                class="w-6 h-6 bg-[#fc3113] text-white rounded-full flex items-center justify-center hover:scale-110 transition-transform duration-200"
                aria-label="View on GitHub"
              >
                <svg class="w-3 h-3" fill="currentColor" viewBox="0 0 24 24">
                  <path
                    d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"
                  />
                </svg>
              </a>
              <a
                v-if="project.demoUrl"
                :href="project.demoUrl"
                target="_blank"
                rel="noopener noreferrer"
                class="w-6 h-6 bg-[#fc3113] text-white rounded-full flex items-center justify-center hover:scale-110 transition-transform duration-200"
                aria-label="View live demo"
              >
                <svg
                  class="w-3 h-3"
                  viewBox="0 0 24 24"
                  fill="currentColor"
                  aria-hidden="true"
                >
                  <path d="M8 5v14l11-7z" />
                </svg>
              </a>
            </div>
          </div>

          <!-- Skills under title -->
          <div class="flex flex-wrap gap-1">
            <span
              v-for="skill in project.skills"
              :key="skill"
              class="bg-[#fc3113]/20 text-[#fc3113] border border-[#fc3113]/30 px-1.5 py-0.5 rounded-full text-xs"
              :style="{ fontFamily: 'JetBrains Mono' }"
            >
              {{ skill }}
            </span>
          </div>
        </div>
      </div>
    </div>

    <!-- Modal for small screens -->
    <div
      v-if="isModalOpen && selectedProject"
      class="fixed inset-0 z-50 flex items-center justify-center p-4 bg-black/80 backdrop-blur-sm"
      @click="closeModal"
    >
      <div
        class="bg-black/90 backdrop-blur-lg border border-[#fc3113] rounded-xl p-6 max-w-md w-full max-h-[90vh] overflow-y-auto relative"
        @click.stop
      >
        <!-- Project preview -->
        <div class="relative overflow-hidden bg-black/20 rounded-lg mb-4">
          <div class="aspect-video relative">
            <img
              :src="selectedProject.preview"
              :alt="`${selectedProject.title} preview`"
              class="w-full h-full object-cover"
            />
          </div>
        </div>

        <!-- Project info -->
        <div class="flex flex-col gap-4 text-left">
          <!-- Title + GitHub link + Demo link (if available) -->
          <div class="flex items-center justify-between gap-3 w-full">
            <h3 class="text-xl font-bold text-white">
              {{ selectedProject.title }}
            </h3>
            <div class="flex items-center gap-2 flex-shrink-0">
              <a
                :href="selectedProject.githubUrl"
                target="_blank"
                rel="noopener noreferrer"
                class="w-8 h-8 bg-[#fc3113] text-white rounded-full flex items-center justify-center hover:scale-110 transition-transform duration-200"
                aria-label="View on GitHub"
                @click.stop
              >
                <svg class="w-4 h-4" fill="currentColor" viewBox="0 0 24 24">
                  <path
                    d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"
                  />
                </svg>
              </a>
              <a
                v-if="selectedProject.demoUrl"
                :href="selectedProject.demoUrl"
                target="_blank"
                rel="noopener noreferrer"
                class="w-8 h-8 bg-[#fc3113] text-white rounded-full flex items-center justify-center hover:scale-110 transition-transform duration-200"
                aria-label="View live demo"
                @click.stop
              >
                <svg
                  class="w-4 h-4"
                  viewBox="0 0 24 24"
                  fill="currentColor"
                  aria-hidden="true"
                >
                  <path d="M8 5v14l11-7z" />
                </svg>
              </a>
            </div>
          </div>

          <!-- Skills under title -->
          <div class="flex flex-wrap gap-2">
            <span
              v-for="skill in selectedProject.skills"
              :key="skill"
              class="bg-[#fc3113]/20 text-[#fc3113] border border-[#fc3113]/30 px-2 py-1 rounded-full text-xs"
              :style="{ fontFamily: 'JetBrains Mono' }"
            >
              {{ skill }}
            </span>
          </div>

          <!-- Divider -->
          <div class="border-t border-[#fc3113]/40"></div>

          <!-- Writeup -->
          <p
            class="text-xs text-white/60 leading-relaxed"
            :style="{ fontFamily: 'JetBrains Mono' }"
          >
            {{ selectedProject.description }}
          </p>
        </div>

        <!-- Close button at bottom center -->
        <div class="flex justify-center mt-6">
          <button
            @click="closeModal"
            class="w-10 h-10 bg-white text-white rounded-full flex items-center justify-center hover:scale-110 transition-transform duration-200"
            aria-label="Close modal"
          >
            <svg
              class="w-5 h-5"
              fill="white"
              stroke="currentColor"
              viewBox="0 0 24 24"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M6 18L18 6M6 6l12 12"
              />
            </svg>
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* Hide scrollbar for Chrome, Safari and Opera */
.overflow-x-auto::-webkit-scrollbar {
  display: none;
}

/* Hide scrollbar for IE, Edge and Firefox */
.overflow-x-auto {
  -ms-overflow-style: none; /* IE and Edge */
  scrollbar-width: none; /* Firefox */
}
</style>
