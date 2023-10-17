<template>
  <div class="grid place-items-center">
    <div
      class="flex min-h-full flex-col justify-center px-4 py-8 lg:py-12 lg:px-8"
    >
      <TheHeader />
      <MacroCalculator />
    </div>
  </div>
</template>

<script setup lang="ts">
const pageTitle = "Macro Calculator";
const seoTitle = "Get your Macros with this simple calculator.";
const seoDesc =
  "Calculate Your Macros: Our user-friendly macro calculator can help you customize your diet, make the most of your macros, and easily reach your fitness and health objectives.";

useHead({
  title: pageTitle,
  link: [{ rel: "icon", type: "image/svg+xml", href: "/favicon.svg" }],
});

useServerSeoMeta({
  title: seoTitle,
  ogTitle: seoTitle,
  twitterTitle: seoTitle,
  description: seoDesc,
  ogDescription: seoDesc,
  twitterDescription: seoDesc,
});
</script>
