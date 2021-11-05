<template>
  <v-card>
    <v-card-title>Blog Posts</v-card-title>
    <v-list v-for="post of posts" :key="post.slug">
      <v-list-item>
        <nuxt-link :to="post.path">{{ post.title }}</nuxt-link>
      </v-list-item>
    </v-list>
  </v-card>
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
  mounted() {
    // eslint-disable-next-line no-console
    console.log(this.posts);
  }
}
</script>