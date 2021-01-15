<template>
  <div class="relative bg-white overflow-hidden">
    <div class="max-w-7xl mx-auto">
      <div class="relative z-10 pb-8 bg-white sm:pb-16 md:pb-20 lg:max-w-4xl lg:w-full lg:pb-28 xl:pb-32">
        <main class="mt-10 mx-auto px-4 sm:mt-12 sm:px-6 md:mt-16 lg:mt-20 lg:px-8 xl:mt-28">
          <div class="sm:text-center lg:text-left">
            <h1 class="text-sm tracking-tight font-extrabold text-gray-900 sm:text-5xl">
              <span class="block xl:inline">People listing</span>
            </h1>
            <div v-if="loading" class="ml-1 my-4">
              <svg class="animate-spin -ml-1 mr-3 h-5 w-5 text-indigo-600 inline" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
                <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
                <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
              </svg>
              <span class="relative text-sm text-indigo-600">Crushing data just for you...</span>
            </div>
          </div>
          <div>
            <div v-if="listing">
              <card v-for="(item, index) of listing" :key="index" :payload="item"></card>
            </div>
          </div>
        </main>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import fetch from 'unfetch'
import Card from '@/components/Card.vue'

export default defineComponent({
  data() {
    return {
      loading: false,
      listing: []
    }
  },
  name: 'Listing',
  components: {
    Card
  },
  methods: {
    async fetchData() {
      this.loading = true
      const response = await fetch('https://swapi.dev/api/people/')
      const data = await response.json()
      this.listing = data?.results
      this.loading = false
    }
  },
  async created() {
    this.fetchData()
  }
})
</script>
