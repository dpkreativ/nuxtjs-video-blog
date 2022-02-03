<template>
  <div class="py-20">
    <section class="px-5">
      <NuxtLink to="/" href="/" class="py-2 text-gray-500 flex items-center">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="none">
          <path
            d="M5.83 11L8.41 8.41L7 7L2 12L7 17L8.41 15.59L5.83 13H22V11H5.83Z"
            fill="currentColor"
          />
        </svg>
        <div class="ml-1">Go back</div>
      </NuxtLink>

      <div class="mt-5">
        <video controls class="w-full" preload="metadata">
          <source :src="post.video" type="video/mp4" />
          <p>Your browser doesn't support HTML5 video.</p>
        </video>
      </div>
      <h1 class="mt-5 font-bold text-3xl">{{ post.title }}</h1>
      <ul v-if="post.tags" class="flex space-x-3 mt-2">
        <li
          v-for="tag in post.tags"
          :key="tag"
          class="px-2 py-1 bg-green-400 text-white text-xs"
        >
          {{ tag }}
        </li>
      </ul>
      <p class="text-gray-500 mt-2 text-sm">{{ post.description }}</p>
      <p class="mt-2 text-gray-500">{{ post.publishDate }}</p>
      <h2 class="mt-2 font-semibold">{{ post.author }}</h2>
    </section>
    <section class="my-5 px-5">
      <nuxt-content :document="post" />
    </section>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const post = await $content(params.slug).fetch()
    return { post }
  },
}
</script>
