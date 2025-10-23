<script setup lang="ts">
import { PhLinkSimple } from "@phosphor-icons/vue";
interface Education {
  id: string;
  school: string;
  logo: string;
  link: string;
  time: string;
  course: string;
  award: string;
}
const education: Education[] = [
  {
    id: "1",
    school: "University of the Philippines - Diliman",
    logo: "/up-seal.png",
    link: "https://upd.edu.ph/",
    time: "Graduated July 2025",
    course: "BS Computer Science",
    award: "Distinction in Leadership as CS Department Representative",
  },
  {
    id: "2",
    school: "Philippine Science High School - Main Campus",
    logo: "/pshs-logo.png",
    link: "https://pshs.edu.ph/",
    time: "Graduated July 2018",
    course: "Secondary Diploma - STEM",
    award: "Distinction in Leadership as founder of CS organization",
  },
];
</script>

<template>
  <section class="">
    <div>
      <h1
        class="text-4xl sm:text-6xl text-left text-[#fc3113] mix-blend-difference"
        :style="{ fontFamily: 'Akira' }"
      >
        EDUCATION
      </h1>
      <div class="w-full h-px border-[#fc3113] bg-[#fc3113]/80"></div>
    </div>
    <!-- Experience Items -->
    <div class="">
      <div
        v-for="(item, index) in education"
        :key="item.id"
        class="group relative"
      >
        <!-- Dot and Timestamp Row -->
        <div
          class="flex items-center gap-4 my-4 md:justify-start justify-center"
        >
          <!-- Timeline Dot -->
          <div
            class="hidden md:block w-2 h-2 rounded-full bg-[#fc3113] flex-shrink-0"
          ></div>

          <!-- Time Badge -->
          <span
            class="bg-[#fc3113] text-black border border-[#fc3113]/30 px-3 py-1 rounded-full text-xs font-mono font-bold"
            style="font-family: 'JetBrains Mono', monospace"
          >
            {{ item.time }}
          </span>
        </div>
        <div
          class="flex items-center gap-4 mb-4 md:justify-start justify-center md:hidden"
        ></div>

        <!-- Education Card -->
        <div
          class="md:ml-6 ml-0 bg-black/80 backdrop-blur-lg border border-[#fc3113]/80 rounded-xl shadow-lg group/card relative p-4"
        >
          <div class="flex flex-col md:flex-row md:items-start items-center">
            <div class="flex flex-row items-start"></div>
            <!-- Content -->
            <div class="flex-grow min-w-0 md:text-left text-center">
              <!-- Header with School, Course, and Time -->
              <div class="">
                <div
                  class="md:text-left text-center flex flex-col md:flex-row items-center"
                >
                  <div class="flex-shrink-0">
                    <img
                      :src="item.logo"
                      :alt="`${item.school} logo`"
                      class="h-16 w-16 object-contain"
                    />
                  </div>
                  <div class="flex flex-col md:ml-4 justify-center">
                    <h3
                      class="md:text-left text-center text-2xl font-bold text-white flex items-center gap-1 md:justify-start justify-center"
                    >
                      <a
                        :href="item.link"
                        target="_blank"
                        rel="noopener noreferrer"
                        class="hover:text-[#fc3113] text-white font-bold transition-colors"
                        @click.stop
                      >
                        {{ item.school }}
                      </a>
                      <PhLinkSimple :size="16" class="text-[#fc3113]" />
                    </h3>
                    <span
                      class="block md:text-left text-center text-xl text-white font-regular"
                    >
                      {{ item.course }}
                    </span>
                  </div>
                </div>
              </div>

              <!-- Award/Description -->
              <div class="max-h-96 opacity-100 translate-y-0 mt-4">
                <div class="text-left pt-4 border-t border-[#fc3113]/40">
                  <ul class="list-none text-sm">
                    <li class="flex items-start gap-2 mb-1">
                      <span
                        class="text-white/60 font-mono text-sm mt-1 flex-shrink-0"
                        >•</span
                      >
                      <span
                        class="text-white/80 leading-relaxed font-mono"
                        style="font-family: 'JetBrains Mono', monospace"
                      >
                        {{ item.award }}
                      </span>
                    </li>
                  </ul>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
