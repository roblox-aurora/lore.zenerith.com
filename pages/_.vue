<template>
  <article>
    <h1 v-if="article.title" class="title">{{ article.title }}</h1>
    <div class="heading">
      <div class="slug">{{ dateUpdated }}</div>
      <div class="github">
        <a
          :href="`https://github.com/roblox-aurora/lore.zenerith.com/edit/master/content${article.path}.md`"
        >
          <font-awesome-icon :icon="['fas', 'pencil-alt']" size="1x" />
        </a>
      </div>
    </div>

    <div
      :class="{
        'two-column':
          article.sidebar !== undefined ||
          siblingArticles !== undefined ||
          sidebar !== undefined,
      }"
    >
      <div v-if="article.sidebar || siblingArticles || sidebar" class="sidebar">
        <pane v-if="sidebar" class="muddy-slate sidebar">
          <nuxt-content :document="sidebar" />
        </pane>
        <pane
          v-if="siblingArticles && siblingArticles.length > 0"
          class="muddy-slate"
        >
          <div v-for="subArticle in siblingArticles" :key="subArticle.slug">
            <nuxt-link
              :to="`${article.dir !== '/' ? article.dir + '/' : '/'}${
                subArticle.slug
              }`"
              >{{ subArticle.title }}</nuxt-link
            >
          </div>
        </pane>
        <pane v-if="typeof article.sidebar === 'object'" class="muddy-slate">
          <div v-for="(link, id) in article.sidebar" :key="link">
            <nuxt-link :to="`${link}`">{{ id }}</nuxt-link>
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
    const fullPath = params.pathMatch || '/index'

    let article = await $content(fullPath ?? '/index').fetch()

    // If folder
    if (Array.isArray(article) && article.length > 0) {
      article = article[0]
    }

    const moment = require('moment')
    const dateUpdated = moment(article.upatedAt).format('LL')
    const siblingArticles = await $content(article.dir).fetch()

    let sidebar
    if (typeof article.sidebar === 'string') {
      sidebar = await $content(article.sidebar).fetch()
    }

    return {
      article,
      sidebar,
      siblingArticles: siblingArticles?.filter((f) => f.showInSidebar),
      fullPath,
      dateUpdated,
    }
  },
}
</script>

<style lang="scss">
article {
  a {
    color: orangered;
    text-decoration: none;
  }
}

article .heading {
  display: flex;
  justify-content: space-between;
  a {
    color: white;
  }
}

article .pane .nuxt-content,
article .pane .nuxt-content-container {
  margin: 0px;
}
hr {
  color: #51473d;
}
</style>
