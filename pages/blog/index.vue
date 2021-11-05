<template>
  <div>
    <h1>Blog Posts</h1>
    <v-list v-for="post of posts" :key="post.slug">
      <v-list-item>
        <nuxt-link :to="post.slug">{{ post.title }}</nuxt-link>
      </v-list-item>
    </v-list>
  </div>
</template>

<script>
export default {
  async asyncData({$content}) {
    const posts = await $content("blog").fetch();
    // eslint-disable-next-line no-console
    console.log(posts);

    return {
      posts,
    }
  },
}
</script>