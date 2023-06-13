<script setup>
import { containerMaxW } from '@/config.js'
</script>

<template>
  <section
    class="p-6 overflow-scroll"
    :class="containerMaxW"
  >
    <slot />
  </section>
</template>
