<script lang="ts" setup>
import NetworkFigures from './NetworkFigures.vue'
</script>

<template>
  <Story
    title="Network Figures"
    :layout="{
      type: 'grid',
      width: 450,
    }"
    group="homepage"
  >
    <template #default>
      <NetworkFigures></NetworkFigures>
    </template>
  </Story>
</template>
