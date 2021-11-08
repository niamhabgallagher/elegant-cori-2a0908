<template>
  <v-card style="margin-left: 10px; margin-right: 10px; margin-top: 20px;">
    <v-btn style="position: fixed; top: 10vh;" icon @click="$router.push('/blog')"><v-icon>mdi-arrow-left</v-icon></v-btn>
    <img v-if="post.thumbnail" style="max-width: inherit;" :src="post.thumbnail"/>
    <v-card-title>{{ post.title }}</v-card-title>
    <v-card-text v-if="post.body">{{ post.body }}</v-card-text>
  </v-card>
</template>

<script>
export default {
  async asyncData({ $content, params, error }) {
    let post;
    try {
      post = await $content("blog", params.slug).fetch();
      // OR const article = await $content(`articles/${params.slug}`).fetch()
    } catch (e) {
      error({ message: "Blog Post not found" });
    }

    return {
      post,
    };
  },
};
</script>