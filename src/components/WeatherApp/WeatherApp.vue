<script setup>
import { ref } from 'vue'
import SearchBar from '@/components/SearchBar/SearchBar.vue'
import WeatherCard from '@/components/WeatherCard/WeatherCard.vue'

const places = ref([])

const addPlace = (data) => {
places.value.push(data)
}
</script>

<template>
    <div class="text-center mb-6">
      {{
        new Date().toLocaleDateString('en-us', {
          weekday: 'long',
          year: 'numeric',
          month: 'long',
          day: 'numeric'
        })
      }}
    </div>

    <div>
      <SearchBar @place-data="addPlace" />
    </div>

    <div class="grid grid-cols-2 gap-4">
      <div v-for="(place, idx) in places" :key="idx">
        <WeatherCard :place="place" />
      </div>
    </div>
</template>