<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <div class="events">
      <EventCard v-for="event in events" :key="event.id" :event="event" />
      <div class="" v-for="event in events" :key="event.id">
          {{event.title}}
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import EventCard from "@/components/EventCard.vue";
import EventService from '@/services/EventService.js'
export default {
  name: "EVentList",
  components: {
    EventCard,
  },
  data() {
    return {
      events: null
    }
  },
  created() {
    EventService.getEvents().then(res => this.events = res.data).catch(err => console.log(err))
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
