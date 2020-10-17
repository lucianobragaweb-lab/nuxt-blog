<template>
  <div>
    {{ $route.params.id }} {{ ip }}
  </div>
</template>

<script>
export default {
  data () {
    return {
      ip: null
    }
  },
  created () {
    this.asyncData()
  },
  methods: {
    async asyncData () {
      const ip = await this.$axios.$get(`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`)
      this.ip = { ip }
    }
  }
}
</script>
