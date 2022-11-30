<template>
  <h1>Events for Good</h1>
  <div class="events">
    <img alt="Vue logo" src="../assets/logo.png" />
    <event-card v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
import EventService from '../services/EventService'
// @ is an alias to /src
import EventCard from "@/components/EventCard.vue";

export default {
  name: "EventList",
  components: {
    EventCard,
  },
  data() {
    return {
      events: null
    }
  },
  created() {
    EventService.getEvents()
      .then(response => {
        this.events = response.data
      })
      .catch(error => {
        console.log(error)
      })
  }
};
</script>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>