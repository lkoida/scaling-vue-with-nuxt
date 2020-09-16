<template>
  <div>
    <div class="title">
      {{ message }}
    </div>
    <p v-if="statusCode === 404">
      <nuxt-link to="/">
        return to home page
      </nuxt-link>
    </p>
  </div>
</template>
<script>
export default {
  name: 'Error',
  props: {
    error: {
      type: Object,
      default: null
    }
  },
  computed: {
    statusCode () {
      return (this.error && this.error.statusCode) || 500
    },
    message () {
      return this.error.message
    }
  },
  head () {
    return {
      title: this.message
    }
  }
}
</script>

<style scoped>

</style>
