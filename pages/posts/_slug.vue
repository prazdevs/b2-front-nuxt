<template>
  <div>
    <h1>{{ title }}</h1>
    <p>{{ body }}</p>
    <p>post: {{ id }}</p>
    <NuxtLink :to="`/posts/${id + 1}`">
      suivant
    </NuxtLink>
  </div>
</template>

<script>
export default {
  async asyncData ({ params, $axios }) {
    const slug = params.slug

    const { title, body, id } = await $axios.$get(`https://jsonplaceholder.typicode.com/posts/${slug}`)

    return { title, body, id, slug }
  }
}
</script>
