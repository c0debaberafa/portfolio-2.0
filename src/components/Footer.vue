<script setup lang="ts">
import {
  PhDiscordLogo,
  PhEnvelopeSimple,
  PhGithubLogo,
  PhXLogo,
  PhFacebookLogo,
  PhInstagramLogo,
  PhSpotifyLogo,
} from "@phosphor-icons/vue";

const currentYear = new Date().getFullYear();
</script>

<template>
  <div class="relative">
    <!-- Full width dark frosted glass background -->
    <div
      class="absolute inset-y-0 bg-[#fc3113] z-20"
      style="
        left: calc(-50vw + 50%);
        right: calc(-50vw + 50%);
        bottom: calc(-50bw +100%);
      "
    ></div>

    <!-- Content with original margins preserved -->
    <div class="relative z-30 py-4">
      <div class="flex flex-col items-center justify-center gap-4">
        <!-- Social Icons Row -->
        <div class="flex gap-2 sm:gap-4">
          <PhEnvelopeSimple
            :size="32"
            weight="fill"
            class="text-black hover:text-white transition-colors duration-200"
          />
          <PhGithubLogo
            :size="32"
            weight="fill"
            class="text-black hover:text-white transition-colors duration-200"
          />
          <PhDiscordLogo
            :size="32"
            weight="fill"
            class="text-black hover:text-white transition-colors duration-200"
          />
          <PhXLogo
            :size="32"
            weight="fill"
            class="text-black hover:text-white transition-colors duration-200"
          />
          <PhFacebookLogo
            :size="32"
            weight="fill"
            class="text-black hover:text-white transition-colors duration-200"
          />
          <PhInstagramLogo
            :size="32"
            weight="fill"
            class="text-black hover:text-white hover:scale-110 transition-all duration-200"
          />
          <PhSpotifyLogo
            :size="32"
            weight="fill"
            class="text-black hover:text-white transition-colors duration-200"
          />
        </div>

        <!-- Copyright Text -->
        <span
          class="font-mono font-bold text-xs text-center text-black"
          :style="{ fontFamily: 'JetBrains Mono' }"
        >
          © Rafa Partosa | All rights reserved 2025
        </span>
      </div>
    </div>
  </div>
</template>
