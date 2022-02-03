<template>
  <Tutorial />
</template>

<script>
export default {
  name: 'IndexPage',
  async asyncData({ $content }) {
    const posts = await $content()
      .only(['title', 'thumbnail', 'tags', 'slug'])
      .sortBy('createdAt', 'desc')
      .fetch()
    console.log('posts', posts)
    return {
      posts,
    }
  },
}
</script>
