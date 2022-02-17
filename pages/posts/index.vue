<template>
  <v-row>
    <v-col v-for="post in posts" :key="post.id" cols="4">
      <v-card>
        <v-card-title>{{ post.title }}</v-card-title>
        <v-card-text>{{ post.body }}</v-card-text>
        <v-card-actions>
          <v-btn nuxt :to="`/posts/${post.id}`">
            Ouvrir
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  async asyncData ({ $axios }) {
    const posts = await $axios.$get('https://jsonplaceholder.typicode.com/posts')

    return { posts }
  }
}
</script>
