<script setup>
import WeatherForecastDay from '@/components/WeatherForecastDay/WeatherForecastDay.vue'

defineProps({
  place: Object
})

</script>

<template>
  <div
    :class="place.current.is_day === 1 ? 'bg-day' : 'bg-night'"
    class="text-white p-10 rounded-lg shadow-lg gap-6 mb-6 relative overflow-hidden"
  >
    <div class="mb-2 flex justify-between items-center">
      <div class="flex items-center justify-center gap-2">
        <i class="fa-solid fa-location-dot"></i>
        <h1 class="text-3xl">{{ place.location.name }}</h1>
      </div>
      <div class="flex items-center justify-center gap-2">
        <i class="fa-solid fa-clock"></i>
        <h1 class="text-3xl">
          {{ new Date(place.location.localtime).getHours() }}:{{
            new Date(place.location.localtime).getMinutes()
          }}
        </h1>
      </div>
    </div>
    <div class="text-center flex-1">
      <img :src="place.current.condition.icon" alt="icon" width="200" class="mx-auto -mb-10" />
      <h1 class="text-9xl mb-2 -mr-4">{{ Math.round(place.current.temp_c) }}&deg;</h1>
      <p class="text-2xl">{{ place.current.condition.text }}</p>
    </div>

    <div class="w-full h-px bg-gradient-to-r from-white/0 via-white/90 to-white/0 my-10"></div>


    <div v-for="(day, idx) in place.forecast.forecastday" :key="idx">
      <WeatherForecastDay :day="day" />
    </div>
  </div>
</template>

<style scoped>
.bg-day {
  background-color: #87CEEB ;
  background-image: linear-gradient(60deg, #87CEEB 0%,#87CEEB 100% );
}
.bg-night {
  background-color: #708090;
  background-image: linear-gradient(60deg, #708090 0%,#708090 100% );
}
</style>