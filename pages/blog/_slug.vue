<script>
  export default {
    async asyncData({ $content, params }) {
      // fetch our article here
        const article = await $content('articles', params.slug).fetch()
        return { article }
    },
    methods: {
        formatDate(date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleDateString('en', options)
     }  

    }
  }
</script>

<template>
  <article>
      <pre> {{ article }} </pre>
      <p>Article last updated: {{ formatDate(article.updatedAt) }}</p>
    <nuxt-content :document="article" />
  </article>
</template>