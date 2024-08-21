<script setup>
import { ref } from 'vue'

defineProps({
  msg: String
})

const count = ref(0)

const fetchedHtml = ref('')

// Fetch data from the endpoint
const fetchData = async () => {
  try {
    const response = await fetch('https://www.biggerpockets.com/shared_components/component?name=membership/dashboard/widgets/trending_topics')
    const result = await response.text()
    fetchedHtml.value = result
  } catch (error) {
    console.error('Failed to fetch data:', error)
  }
}

await fetchData()

</script>

<template>
  <h1>{{ msg }}</h1>
  <div v-html="fetchedHtml"></div>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
