<template>
  <div class="text-center">
    <h1 class="text-4xl mt-[120px] font-extrabold tracking-tight sm:text-5xl lg:text-6xl bg-gradient-to-r from-[#6209F6] via-[#DC8AF6] to-[#83D0FB] text-transparent bg-clip-text py-2">
      <span class="block">{{ title }}</span>
    </h1>
    <p v-if="subtitle2" class="text-2xl  font-extrabold tracking-tight sm:text-5xl lg:text-2xl bg-gradient-to-r from-banana-primary-yellow to-banana-secondary-blue text-transparent bg-clip-text py-2">
      {{ subtitle2 }}
    </p>
    <p v-if="subtitle" class="mx-auto mt-6 max-w-5xl text-lg tracking-tight text-banana-text-muted">
      {{ subtitle }}
    </p>

  </div>
</template>

<script setup lang="ts">
interface Props {
  title: string
  subtitle: string
  subtitle2?: string
}

defineProps<Props>()
</script> 