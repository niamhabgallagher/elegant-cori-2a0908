<template>
  <v-app dark>
    <v-app-bar
      app
      absolute
    >
        <v-toolbar-title>
            <v-icon>mdi-heart</v-icon>
            My New Website
        </v-toolbar-title>
      <v-spacer />
      <v-btn icon>
        <v-icon>mdi-account-cog</v-icon>
      </v-btn>

      <template v-slot:extension>
        <v-tabs align-with-title>
          <v-tab to="/">Welcome</v-tab>
          <v-tab to="/blog">Blog</v-tab>
        </v-tabs>
      </template>
    </v-app-bar>

    <v-main
      style="margin-top: 15px">
      <v-content>
        <Nuxt />
      </v-content>
    </v-main>

    <v-footer
      app
    >
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      items: [
        {
          title: 'Welcome',
          to: '/'
        },
        {
            title: 'Blog',
            to: '/blog'
        }
      ],
    }
  },
  head() {
    return {
      script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }],
    };
  },
}
</script>
