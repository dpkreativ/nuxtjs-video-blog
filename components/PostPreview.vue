<template>
  <div>
    <a :href="`/blog/${post.slug}`">
      <div class="w-full max-w-sm h-64 overflow-hidden rounded-lg">
        <img
          :src="post.thumbnail"
          alt="blogpost preview"
          class="object-cover w-full h-full"
        />
      </div>
      <ul v-if="post.tags" class="flex space-x-3 mt-2">
        <li v-for="tag in post.tags" :key="tag">{{ tag }}</li>
      </ul>
      <h2 class="font-semibold text-xl mt-2">{{ post.title }}</h2>
    </a>
  </div>
</template>

<script>
export default {
  props: {
    post: Object,
  },
}
</script>
