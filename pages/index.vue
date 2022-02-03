<template>
  <main>
    <section>
      <h1 class="font-bold text-center text-5xl">My Nuxt Video Blog</h1>
    </section>
    <section v-for="post in posts" :key="post.title">
      <h2 class="font-semibold text-xl">{{ post.title }}</h2>
    </section>
  </main>
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
