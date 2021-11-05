<template>
  <div>
    <h2>{{ post.title }}</h2>
    <img v-if="post.thumbnail" :src="post.thumbnail"/>
    <p v-if="post.body">{{ post.body }}</p>
  </div>
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