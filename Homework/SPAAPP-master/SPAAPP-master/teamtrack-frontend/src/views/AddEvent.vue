<template>
    <navbar />
  <AddEventForm :event="event" />
</template>

<script setup lang="ts">
import AddEventForm from "@/components/AddEventForm.vue";
    import { Event } from '@/models/event';
    import navbar from "../components/Navbar.vue"
import { ref } from 'vue';

const event = ref<Event>({
  id: 0,
  type: "",
  description: "",
  location: "",
  date: new Date().toISOString(),
});
</script>