<template>
  <div>
    <h1>{{ title }}</h1>
    <p>{{ body }}</p>
    <p>post: {{ id }}</p>
    <NuxtLink :to="`/posts/${id + 1}`">
      suivant
    </NuxtLink>
    <v-list>
      <v-list-item v-for="comment in comments" :key="comment.id" two-line>
        <v-list-item-content>
          <v-list-item-title>
            <span class="text-overline">{{ comment.email }}</span> - {{ comment.name }}
          </v-list-item-title>
          <v-list-item-subtitle>{{ comment.body }}</v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </div>
</template>

<script>
export default {
  async asyncData ({ params, $axios }) {
    const slug = params.slug

    const url = `https://jsonplaceholder.typicode.com/posts/${slug}`

    const { title, body, id } = await $axios.$get(url)
    const comments = await $axios.$get(`${url}/comments`)

    return { title, body, id, comments }
  }
}
</script>
