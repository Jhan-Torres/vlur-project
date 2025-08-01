<script setup lang="ts">
import { Sparkles, Play, BookOpen, Users, ArrowRight } from "lucide-vue-next";
import { useTranslations } from "../../../shared/hooks/useTranslations";

interface Props {
  hasRecommendations: boolean;
}

interface Emits {
  (e: "get-started"): void;
  (e: "show-community"): void;
  (e: "scroll-to-features"): void;
}

defineProps<Props>();
defineEmits<Emits>();

const { t } = useTranslations();
</script>

<template>
  <section class="relative overflow-hidden">
    <div class="container-main py-12 relative z-10 sm:py-20">
      <div class="text-center">
        <div class="mb-6 sm:mb-8">
          <div
            class="inline-flex items-center px-3 py-2 bg-blue-100/90 backdrop-blur-sm rounded-full text-blue-600 text-xs font-medium mb-4 border border-blue-200/50 dark:bg-blue-900/50 dark:text-blue-400 dark:border-blue-700/50 sm:px-4 sm:text-sm sm:mb-6"
          >
            <Sparkles class="h-3 w-3 mr-2 sm:h-4 sm:w-4" />
            {{ hasRecommendations ? t("welcomeBack") : t("heroTag") }}
          </div>
        </div>

        <h1
          class="text-hero text-gray-900 mb-4 leading-tight drop-shadow-sm dark:text-white sm:mb-6"
        >
          {{ hasRecommendations ? t("welcomeBackTitle") : t("heroTitle") }}
          <span
            class="bg-gradient-to-r from-blue-600 to-indigo-600 bg-clip-text text-transparent block"
          >
            {{ t("heroSubtitle") }}
          </span>
        </h1>

        <p
          class="text-subtitle text-gray-600 mb-8 max-w-3xl mx-auto leading-relaxed drop-shadow-sm px-4 dark:text-gray-300 sm:mb-10"
        >
          {{
            hasRecommendations
              ? t("welcomeBackDescription")
              : t("heroDescription")
          }}
        </p>

        <div class="btn-group-vertical justify-center items-center px-4">
          <button
            @click="$emit('get-started')"
            class="w-full px-6 py-3 bg-gradient-to-r from-blue-500 to-indigo-500 text-white rounded-xl font-semibold text-base hover:from-blue-600 hover:to-indigo-600 transform hover:scale-105 transition-all duration-200 shadow-xl backdrop-blur-sm sm:w-auto sm:px-8 sm:py-4 sm:text-lg"
          >
            <component
              :is="hasRecommendations ? ArrowRight : Play"
              class="inline h-4 w-4 mr-2 sm:h-5 sm:w-5"
            />
            {{ hasRecommendations ? t("continueJourney") : t("startNow") }}
          </button>
          <button
            @click="$emit('show-community')"
            class="w-full px-6 py-3 bg-gradient-to-r from-purple-500 to-pink-500 text-white rounded-xl font-semibold text-base hover:from-purple-600 hover:to-pink-600 transform hover:scale-105 transition-all duration-200 shadow-xl backdrop-blur-sm sm:w-auto sm:px-8 sm:py-4 sm:text-lg"
          >
            <Users class="inline h-4 w-4 mr-2 sm:h-5 sm:w-5" />
            {{ t("exploreCommunity") }}
          </button>
          <button
            @click="$emit('scroll-to-features')"
            class="w-full px-6 py-3 bg-white/80 backdrop-blur-sm text-gray-700 rounded-xl font-semibold text-base hover:bg-white/90 transition-all duration-200 border border-gray-200/50 shadow-lg dark:bg-gray-800/80 dark:text-gray-300 dark:hover:bg-gray-800/90 dark:border-gray-700/50 sm:w-auto sm:px-8 sm:py-4 sm:text-lg"
          >
            <BookOpen class="inline h-4 w-4 mr-2 sm:h-5 sm:w-5" />
            {{ t("learnMore") }}
          </button>
        </div>

        <!-- Community Stats for all users -->
        <div
          class="mt-8 grid grid-cols-1 gap-4 max-w-2xl mx-auto px-4 sm:mt-12 sm:grid-cols-3 sm:gap-6"
        >
          <div class="card-primary">
            <div
              class="text-xl font-bold text-purple-600 dark:text-purple-400 sm:text-2xl"
            >
              2.5K+
            </div>
            <div class="text-xs text-gray-600 dark:text-gray-400 sm:text-sm">
              {{ t("communityMembers") }}
            </div>
          </div>
          <div class="card-primary">
            <div
              class="text-xl font-bold text-indigo-600 dark:text-indigo-400 sm:text-2xl"
            >
              15K+
            </div>
            <div class="text-xs text-gray-600 dark:text-gray-400 sm:text-sm">
              {{ t("sharedRecommendations") }}
            </div>
          </div>
          <div class="card-primary">
            <div
              class="text-xl font-bold text-cyan-600 dark:text-cyan-400 sm:text-2xl"
            >
              4.8★
            </div>
            <div class="text-xs text-gray-600 dark:text-gray-400 sm:text-sm">
              {{ t("communityRating") }}
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Floating Elements -->
    <div class="absolute top-20 left-10 opacity-20 z-10 dark:opacity-10">
      <div
        class="w-12 h-12 bg-blue-500 rounded-full blur-xl animate-pulse sm:w-20 sm:h-20"
      ></div>
    </div>
    <div class="absolute top-40 right-20 opacity-20 z-10 dark:opacity-10">
      <div
        class="w-20 h-20 bg-indigo-500 rounded-full blur-xl animate-pulse delay-1000 sm:w-32 sm:h-32"
      ></div>
    </div>
    <div class="absolute bottom-20 left-1/4 opacity-20 z-10 dark:opacity-10">
      <div
        class="w-10 h-10 bg-cyan-500 rounded-full blur-xl animate-pulse delay-500 sm:w-16 sm:h-16"
      ></div>
    </div>
  </section>
</template>
