<template>
  <div
    class="grid place-items-center h-screen bg-neutral-50 text-neutral-900 dark:bg-neutral-900 dark:text-neutral-50"
  >
    <div class="flex min-h-full flex-col justify-center px-4 py-12 lg:px-8">
      <TheHeader />
      <MacroCalculator />
    </div>
  </div>
</template>

<script setup lang="ts">
useHead({
  title: "Macro Calculator",
});

useServerSeoMeta({
  title: "Get your Macros with this simple calculator.",
  ogTitle: "Get your Macros with this simple calculator.",
  twitterTitle: "Get your Macros with this simple calculator.",
  description:
    "Calculate Your Macros: Our user-friendly macro calculator can help you customize your diet, make the most of your macros, and easily reach your fitness and health objectives.",
  ogDescription:
    "Calculate Your Macros: Our user-friendly macro calculator can help you customize your diet, make the most of your macros, and easily reach your fitness and health objectives.",
  twitterDescription:
    "Calculate Your Macros: Our user-friendly macro calculator can help you customize your diet, make the most of your macros, and easily reach your fitness and health objectives.",
});
</script>
