<template>
  <navbar />
  <AddEventForm :event="event" />
</template>

<script setup lang="ts">
import AddEventForm from '@/components/UpdateEvent.vue';
import { Event } from '@/models/event';
import { useEventsStore } from '@/stores/eventsStore';
import { onMounted, ref } from 'vue';
import navbar from "../components/Navbar.vue"
import { useRoute } from 'vue-router'; 

const { load, getEventById } = useEventsStore();
const route = useRoute();

const event = ref<Event>({
  id: 0,
  type: "",
  description: "",
  location: "",
  date: new Date().toISOString(),
});

onMounted(async () => {
  await load();
  const eventId = Number(route.params.id);
  const loadedEvent = getEventById(eventId);
  if (loadedEvent) {
    event.value = { ...loadedEvent };
  }
});
</script>
