<template>
  <article>
    <h1 v-if="article.title" class="title">{{ article.title }}</h1>
    <div class="heading">
      <div class="slug">{{ dateUpdated }}</div>
      <div class="github">
        <a
          :href="`https://github.com/roblox-aurora/lore.zenerith.com/edit/master/content/${article.slug}.md`"
        >
          <font-awesome-icon :icon="['fas', 'pencil-alt']" size="1x" />
        </a>
      </div>
    </div>
    <!-- {{article.toc}} -->

    <div
      :class="{
        'two-column':
          article.sidebar !== undefined || siblingArticles !== undefined,
      }"
    >
      <div v-if="article.sidebar || siblingArticles" class="sidebar">
        <pane v-if="siblingArticles" class="muddy-slate">
          <div v-for="subArticle in siblingArticles" :key="subArticle.slug">
            <nuxt-link :to="`${subArticle.slug}`">{{
              subArticle.title
            }}</nuxt-link>
          </div>
        </pane>
        <!-- <pane v-if="typeof article.sidebar === 'object'" class="muddy-slate">
          <div v-for="(link, id) in article.sidebar" :key="link">
            <nuxt-link :to="`${link}`">{{ id }}</nuxt-link>
          </div>
        </pane> -->
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
    const moment = require('moment')
    const dateUpdated = moment(article.upatedAt).format('LL')
    const siblingArticles = await $content().fetch()

    return {
      article,
      siblingArticles: siblingArticles?.filter((f) => f.showInSidebar),
      slug: `/${params.slug ?? ''}`,
      dateUpdated,
    }
  },
}
</script>

<style lang="scss">
article .heading {
  display: flex;
  justify-content: space-between;
  a {
    color: white;
  }
}
</style>
