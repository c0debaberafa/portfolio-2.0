<script setup lang="ts">
import { ref, computed } from "vue";
import TechCard from "./TechCard.vue";
import Card from "./Card.vue";
type TechCategory =
  | "languages"
  | "frontend"
  | "backend"
  | "tools"
  | "mobile"
  | "ml"
  | "design"
  | "db"
  | "testing"
  | "platform";

type TechItem = {
  name: string;
  imgSrc: string;
  categories: TechCategory[];
  color?: string;
};
const techItems = ref<TechItem[]>([
  {
    name: "Python",
    imgSrc: "/techstack/python.svg",
    categories: ["backend", "languages"],
  },
  {
    name: "C++",
    imgSrc: "/techstack/c-plus-plus.svg",
    categories: ["backend", "languages"],
  },
  {
    name: "Rust",
    imgSrc: "/techstack/rust-light.svg",
    categories: ["backend", "languages"],
  },
  {
    name: "HTML5",
    imgSrc: "/techstack/html5.svg",
    categories: ["frontend", "languages"],
  },
  {
    name: "CSS3",
    imgSrc: "/techstack/css3.svg",
    categories: ["frontend", "languages"],
  },
  {
    name: "Tailwind CSS",
    imgSrc: "/techstack/tailwindcss.svg",
    categories: ["frontend"],
  },
  {
    name: "JavaScript",
    imgSrc: "/techstack/javascript.svg",
    categories: ["frontend", "languages"],
  },
  {
    name: "TypeScript",
    imgSrc: "/techstack/typescript.svg",
    categories: ["frontend", "languages"],
  },
  {
    name: "Vue.js",
    imgSrc: "/techstack/vuejs.svg",
    categories: ["frontend"],
  },
  {
    name: "Nuxt.js",
    imgSrc: "/techstack/nuxtjs.svg",
    categories: ["frontend"],
  },
  {
    name: "React",
    imgSrc: "/techstack/reactjs.svg",
    categories: ["frontend"],
  },
  {
    name: "Vite",
    imgSrc: "/techstack/vitejs.svg",
    categories: ["frontend", "tools"],
  },
  {
    name: "Vitest",
    imgSrc: "/techstack/vitest.svg",
    categories: ["testing", "tools"],
  },
  {
    name: "Playwright",
    imgSrc: "/techstack/playwright.svg",
    categories: ["testing", "tools"],
  },
  {
    name: "Node.js",
    imgSrc: "/techstack/nodejs.svg",
    categories: ["backend"],
  },
  { name: "MySQL", imgSrc: "/techstack/mysql.svg", categories: ["db"] },
  {
    name: "TensorFlow",
    imgSrc: "/techstack/tensorflow.svg",
    categories: ["ml"],
  },
  {
    name: "Next.js",
    imgSrc: "/techstack/nextjs.svg",
    categories: ["frontend", "backend"],
  },
  {
    name: "Supabase",
    imgSrc: "/techstack/supabase.svg",
    categories: ["backend", "db", "platform"],
  },
  {
    name: "Vercel",
    imgSrc: "/techstack/vercel-light.svg",
    categories: ["platform", "tools"],
  },
  {
    name: "Apple",
    imgSrc: "/techstack/apple-light.svg",
    categories: ["tools"],
  },
  {
    name: "Linux",
    imgSrc: "/techstack/linux.svg",
    categories: ["tools", "platform"],
  },
  { name: "Git", imgSrc: "/techstack/git.svg", categories: ["tools"] },
  {
    name: "Figma",
    imgSrc: "/techstack/figma.svg",
    categories: ["design", "tools"],
  },
  {
    name: "Photoshop",
    imgSrc: "/techstack/photoshop.svg",
    categories: ["design", "tools"],
  },
  {
    name: "Lightroom",
    imgSrc: "/techstack/lightroom.svg",
    categories: ["design", "tools"],
  },
  {
    name: "Notion",
    imgSrc: "/techstack/notion.svg",
    categories: ["tools"],
  },
  { name: "Slack", imgSrc: "/techstack/slack.svg", categories: ["tools"] },
  {
    name: "Haskell",
    imgSrc: "/techstack/haskell.svg",
    categories: ["languages"],
  },
  {
    name: "Kotlin",
    imgSrc: "/techstack/kotlin.svg",
    categories: ["languages"],
  },
  {
    name: "Pinia",
    imgSrc: "/techstack/pinia.svg",
    categories: ["frontend"],
  },
]);
const selectedCategory = ref<TechCategory | "all">("all");
const categories = computed(() => {
  const set = new Set<TechCategory>();
  techItems.value.forEach((t) => t.categories.forEach((c) => set.add(c)));
  return ["all", ...Array.from(set)];
});
const filteredTech = computed(() => {
  if (selectedCategory.value === "all") return techItems.value;
  return techItems.value.filter((t) =>
    t.categories.includes(selectedCategory.value as TechCategory)
  );
});
</script>

<template>
  <!-- Tech stack -->
  <section class="relative flex flex-col justify-center">
    <!-- Title -->
    <h1
      class="text-4xl sm:text-6xl text-center md:text-left text-[#fc3113] mix-blend-difference"
      :style="{ fontFamily: 'Akira' }"
    >
      TECH STACK
    </h1>
    <div class="w-full h-px border-[#fc3113] bg-[#fc3113]/80 mb-4"></div>

    <!-- Category buttons -->
    <div
      class="flex gap-2 mb-2 flex-wrap items-center justify-center md:justify-start"
    >
      <button
        v-for="cat in categories"
        :key="cat as string"
        @click="selectedCategory = cat as any"
        class="font-mono font-bold text-xs backdrop-blur-md hover:backdrop-blur-lg border rounded-full px-2 py-1 whitespace-nowrap transition-all duration-300"
        :class="{
          'text-white border-white': cat === selectedCategory,
          'text-[#fc3113] bg-black/80 border-[#fc3113] hover:bg-black/20 hover:border-white hover:text-white':
            cat !== selectedCategory,
        }"
        :style="{ fontFamily: 'JetBrains Mono' }"
      >
        {{ cat }}
      </button>
    </div>

    <div class="relative">
      <!-- Scrollable container -->
      <div
        class="overflow-x-auto"
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
          class="flex gap-4 py-2 justify-start"
          style="width: max-content; min-width: 100%"
        >
          <TechCard
            v-for="tech in filteredTech"
            :key="tech.name"
            :name="tech.name"
            :img-src="tech.imgSrc"
            :font="'JetBrains Mono'"
          />
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
