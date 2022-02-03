<template>
  <main>
    <section class="py-5">
      <h1 class="font-bold text-center text-5xl">My Nuxt Video Blog</h1>
    </section>
    <section class="p-5 grid gap-5 md:grid-cols-2 lg:grid-cols-3">
      <PostPreview
        v-for="post in posts"
        :key="post.slug"
        :post="post"
      ></PostPreview>
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
