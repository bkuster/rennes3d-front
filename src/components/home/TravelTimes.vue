<script setup lang="ts">
import { reactive, onMounted } from 'vue'

import { apiClientService } from '@/services/api.client'
import UiTravelTime from '../ui/UiTravelTime.vue'
import type { TravelTimeModel } from '@/model/travel-time.model'

const state = reactive({
  travelTimes: null as null | TravelTimeModel[],
})

onMounted(async () => {
  state.travelTimes = await apiClientService.fetchTravelTime()
})
</script>

<template>
  <div class="font-dm-sans font-bold text-lg leading-6 text-neutral-400">
    Vos temps de parcours bientot réduits
  </div>
  <div class="flex flex-row items-start p-0 gap-3 overflow-x-auto">
    <UiTravelTime
      v-for="travelTime in state.travelTimes"
      :key="travelTime.line"
      :newDuration="travelTime.new"
      :oldDuration="travelTime.old"
      :lineNumber="travelTime.line"
      :startStation="travelTime.start"
      :endStation="travelTime.end"
    >
    </UiTravelTime>
  </div>
  <a href="">Voir plus</a>
</template>
