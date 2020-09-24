<template>
  <article>
    <h1 v-if="article.title" class="title">{{ article.title }}</h1>
    <div class="slug">{{ slug }}</div>

    <div :class="{ 'two-column': article.sidebar !== undefined }">
      <div v-if="article.sidebar" class="sidebar">
        <pane class="muddy-slate">
          <div v-for="(link, id) in article.sidebar" :key="link">
            <nuxt-link :to="`${slug}${link}`">{{ id }}</nuxt-link>
          </div>
        </pane>
      </div>
      <div class="content">
        <nuxt-content :document="article" />
      </div>
    </div>
  </article>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const article = await $content(params.slug ?? 'index').fetch()

    return { article, slug: `/${params.slug ?? ''}` }
  },
}
</script>
