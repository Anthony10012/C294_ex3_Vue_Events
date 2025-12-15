<script setup>
import TheWelcome from '../components/TheWelcome.vue'
import EventCard from '@/components/EventCard.vue'
import { ref } from 'vue'

const events = ref([
  {
    id: 1,
    time: '18:00',
    date: '2025-12-10',
    title: 'Soirée jeux de société',
  },
  {
    id: 2,
    time: '14:30',
    date: '2025-12-15',
    title: 'Atelier Vue 3',
  },
  {
    id: 3,
    time: '09:00',
    date: '2025-12-20',
    title: 'Petit-déjeuner de classe',
  },
])
</script>

<template>
  <div class="events">
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
