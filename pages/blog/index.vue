<template>
  <v-card style="margin-top: 20px;">
    <v-card-title>Blog Posts</v-card-title>
    <v-list>
      <v-list-item v-for="post of posts" :key="post.slug" :to="post.path">
        <v-list-item-content>
          <v-list-item-title>{{ post.title }}</v-list-item-title>
          <v-list-item-subtitle style="max-width: 200px;">{{ post.body }}</v-list-item-subtitle>
        </v-list-item-content>
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