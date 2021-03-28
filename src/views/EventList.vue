<template>
  <div>
    <h1>Events Listing</h1>
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
import EventCard from "../components/EventCard.vue";
import EventService from "../services/EventService.js";

export default {
  async created() {
    try {
      const req = await EventService.getEvents();
      const response = await req.data;
      this.events = response;
    } catch (e) {
      console.log(e.message);
    }
  },
  data() {
    return {
      events: [],
    };
  },
  components: {
    EventCard,
  },
};
</script>

<style></style>
