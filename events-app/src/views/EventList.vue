<script setup>
import TheWelcome from '../components/TheWelcome.vue'
import EventCard from '@/components/EventCard.vue'
import EventService from '@/services/EventService.js'
import { ref, onMounted } from 'vue'
import axios from 'axios'

const events = ref([])
const isLoading = ref(false)
const error = ref(null)

onMounted(async () => {
  isLoading.value = true
  error.value = null
  try {
    const response = await EventService.getEvents()
    events.value = response.data
  } catch (err) {
    console.error(err)
    error.value = 'Impossible de charger les événements.'
  } finally {
    isLoading.value = false
  }
})
</script>

<template>
  <div class="events">
    <div v-if="error" class="error-message">
      {{ error }}
      <p>Vérifiez si votre URL GitHub est correcte et si le fichier JSON est accessible.</p>
    </div>
    <div v-else-if="isLoading" class="loading-message">Chargement des événements en cours...</div>
    <div v-else>
      <EventCard v-for="event in events" :key="event.id" :event="event" />
    </div>
  </div>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.error-message {
  color: red;
  border: 1px solid red;
  padding: 15px;
  text-align: center;
}
.loading-message {
  padding: 20px;
  font-weight: bold;
  color: #3f9e42;
}
</style>
