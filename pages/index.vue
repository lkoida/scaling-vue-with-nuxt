<template>
  <div>
    <h1>Events</h1>
    <EventCard
      v-for="(event, index) in events"
      :key="index"
      :event="event"
      :data-index="index"
    />
  </div>
</template>
<script>
import EventCard from '@/components/EventCard'
import { mapGetters } from 'vuex'

export default {
  components: {
    EventCard
  },
  async fetch ({ store, error }) {
    try {
      await store.dispatch('events/fetchEvents')
    } catch (e) {
      error({
        statusCode: 503,
        message: 'Events are not available at the moment'
      })
    }
  },
  computed: {
    ...mapGetters({
      events: 'events/events'
    })
  },
  head () {
    return {
      title: 'Event Listing'
    }
  }
}
</script>
