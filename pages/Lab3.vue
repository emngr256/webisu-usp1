<template>
  <div class="container mx-auto p-6 bg-gray-100 min-h-screen">
    <h1 class="text-3xl font-bold text-center mb-8 text-blue-800">🎮 My favourite games</h1>
    
    <div class="mb-6 p-4 bg-white rounded-lg shadow">
      <h2 class="text-lg font-semibold mb-3">Filter by genre:</h2>
      <div class="flex flex-wrap gap-4">
        <label v-for="genre in genres" :key="genre" class="flex items-center space-x-2 cursor-pointer">
          <input 
            type="radio" 
            v-model="selectedGenre" 
            :value="genre"
            class="text-blue-600 focus:ring-blue-500"
          >
          <span class="text-gray-700">{{ genre }}</span>
        </label>
      </div>
    </div>

    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
      <div 
        v-for="game in filteredGames" 
        :key="game.id"
        class="game-card bg-white rounded-xl shadow-lg overflow-hidden hover:shadow-xl transition-shadow duration-300"
      >
        <img 
          :src="game.image" 
          :alt="game.title"
          class="w-full h-38 object-cover"
        >
        <div class="p-4">
          <h3 class="text-xl font-bold text-gray-800 mb-2">{{ game.title }}</h3>
          <div class="space-y-1 text-sm text-gray-600">
            <p><span class="font-semibold">Genre:</span> {{ game.genre }}</p>
            <p><span class="font-semibold">Platform:</span> {{ game.platform }}</p>
            <p><span class="font-semibold">Year:</span> {{ game.releaseYear }}</p>
            <p><span class="font-semibold">My score:</span> 
              <span class="text-yellow-500">{{ '★'.repeat(game.rating) }}</span>
              <span class="text-gray-400">{{ '★'.repeat(10 - game.rating) }}</span>
            </p>
          </div>
        </div>
      </div>
    </div>

    <div v-if="filteredGames.length === 0" class="text-center py-8">
      <p class="text-xl text-gray-500">Game not found 🎯</p>
    </div>
  </div>
</template>

<script setup>
import { reactive, computed, ref } from 'vue'

// Games
const games = reactive([
  {
    id: 1,
    title: "Fallout: New Vegas",
    image: "/img/fnv.jpg", 
    genre: "RPG",
    platform: "Multiplatform",
    releaseYear: 2010,
    rating: 10
  },
  {
    id: 2,
    title: "Gothic II",
    image: "/img/gothic.jpg",
    genre: "RPG", 
    platform: "PC",
    releaseYear: 2002,
    rating: 10
  },
  {
    id: 3,
    title: "Cyberpunk 2077",
    image: "/img/cyberpunk.jpg", 
    genre: "RPG",
    platform: "Multiplatform",
    releaseYear: 2020,
    rating: 8
  },
  {
    id: 4,
    title: "Elden Ring",
    image: "/img/eldenring.jpg",
    genre: "Souls-like",
    platform: "Multiplatform",
    releaseYear: 2022,
    rating: 9
  },
  {
    id: 5,
    title: "Dark Souls III",
    image: "/img/DS3.jpg", 
    genre: "Souls-like",
    platform: "Multiplatform",
    releaseYear: 2016,
    rating: 8
  },
  {
    id: 6,
    title: "Heart of Iron IV",
    image: "/img/hoi.jpg", 
    genre: "Strategy",
    platform: "PC",
    releaseYear: 2016,
    rating: 8
  },

])

const selectedGenre = ref('All')
const selectedPlatform = ref('All')

const genres = computed(() => {
  const uniqueGenres = [...new Set(games.map(game => game.genre))]
  return ['All', ...uniqueGenres]
})

const platforms = computed(() => {
  const uniquePlatforms = [...new Set(games.map(game => game.platform))]
  return ['All', ...uniquePlatforms]
})

const filteredGames = computed(() => {
  return games.filter(game => {
    const genreMatch = selectedGenre.value === 'All' || game.genre === selectedGenre.value
    const platformMatch = selectedPlatform.value === 'All' || game.platform === selectedPlatform.value
    return genreMatch && platformMatch
  })
})
</script>

<style scoped>
.game-card {
  transition: transform 0.2s ease-in-out;
}

.game-card:hover {
  transform: translateY(-5px);
}

.container {
  @apply max-w-7xl;
}

input[type="radio"] {
  @apply w-4 h-4;
}
</style>