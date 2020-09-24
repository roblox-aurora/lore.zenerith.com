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

    return { article, slug: `/wiki/${params.slug ?? ''}` }
  },
}
</script>

<style lang="scss">
article {
  max-width: 1500px;
  margin: 15px auto;
  color: white;

  .slug {
    margin: 10px;
  }

  .two-column {
    display: grid;
    grid-template-columns: 20% 80%;

    column-gap: 10px;

    .sidebar {
      .pane {
        padding: 10px;
      }

      a {
        color: #f8f8f8;
        text-decoration: none;
        font-size: 20px;
      }
    }
  }

  h1 {
    font-size: 25px;

    &.title {
      font-size: 30px;
    }
  }

  p {
    padding: 5px;
  }
}
</style>
