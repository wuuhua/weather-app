<script setup>
import { Cloud } from '@iconoir/vue'
import { storeToRefs } from 'pinia';
import { useWeatherStore } from '../stores/currentWeather'

const weatherStore = useWeatherStore()
const { currentWeather } = storeToRefs(weatherStore)

// 抓取天氣API天氣的對應icon
// `https://openweathermap.org/img/wn/${ currentWeather.weather[0].icon }@2x.png`
</script>

<template>
    <div class="flex flex-col items-center mt-10 gap-y-4">
        <!-- <Cloud color="#ded8d8" height="60" width="60" /> -->
        <div v-if="currentWeather">
            <img :src="`https://openweathermap.org/img/wn/${ currentWeather.weather[0].icon }@2x.png`">
        </div>
        <div v-else>
            <img :src="`https://openweathermap.org/img/wn/10d@2x.png`">
        </div>
        <div v-if="currentWeather">
            <p class="text-6xl font-bold text-white">{{ currentWeather.temp }}°</p>
            <p class="text-xl text-gray-300">{{ currentWeather.weather[0].description }}</p>
        </div>
        <div v-else>
            <p class="text-6xl font-bold text-white">26.73°</p>
            <p class="text-xl text-gray-300">clouds</p>
        </div>
    </div>
</template>