<template>
  <div>
    <ul>
      <li v-for="post in posts" :key="post.id">
        <nuxt-link :to="`/${post.id}/${ getSlug(post.title) }`">{{ post.title }}</nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
import slugify from 'slugify'
export default {
  data () {
    return {
      posts: []
    }
  },
  created () {
    this.asyncData()
  },
  methods: {
    async asyncData () {
      const posts = await this.$axios.$get('https://jsonplaceholder.typicode.com/posts')
      this.posts = posts
    },
    getSlug (slug) {
      return slugify(slug)
    }
  }
}
</script>
