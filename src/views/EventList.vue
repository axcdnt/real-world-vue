<template>
  <div>
    <h1>Events Listing</h1>
    <!-- <EventCard v-for="event in events" :key="event.id" :event="event" /> -->
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
import EventCard from "@/views/EventCard.vue";
import EventService from "@/services/EventService.js";

export default {
  components: {
    EventCard
  },
  data() {
    return {
      events: []
    };
  },
  created() {
    EventService.getEvents("http://localhost:3000/events")
      .then(response => (this.events = response.data))
      .catch(error => console.log(error));
  }
};
</script>

<style></style>
