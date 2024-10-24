<script setup lang="ts">
const { loggedIn } = useUserSession();

watch(loggedIn, async () => {
  if (!loggedIn.value) {
    await navigateTo("/login");
  }
});

useHead({
  htmlAttrs: { lang: "pt-BR" }
});

const items = [[]];
</script>

<template>
  <div class="p-2 flex flex-col gap-4">
    <NuxtRouteAnnouncer />

    <header class="flex justify-between">
      <h1 class="text-black text-2xl">Receitas</h1>

      <UDropdown :items="items" :popper="{ placement: 'bottom-start' }">
        <UButton color="white" icon="i-heroicons-ellipsis-vertical-16-solid" />
      </UDropdown>
    </header>
    <main><NuxtPage /></main>

    <UNotifications />
  </div>
</template>

<style>
:root {
  --bg: #f4f0e8;
}

html,
body {
  height: 100%;
  width: 100%;
  margin: 0;
}

html {
  font-family: "Sometype Mono Variable", monospace !important;
  font-style: normal;
  font-display: optional;
  background: var(--bg);
  font-size: clamp(14px, 1.5vw, 16px);
}

@supports (font-variation-settings: normal) {
  html {
    font-variation-settings: "wdth" 75, "wght" 400 700;
  }
}
</style>
