<template>
  <div class="container">
    <div>
      <Logo />
      <h1 class="title">Zenerith Lore</h1>
      <div class="links">
        <a href="/wiki" rel="noopener noreferrer" class="button--grey">
          Wiki
        </a>
      </div>
      <div
        v-for="article in articles"
        :class="'link-' + article.slug"
        :key="article.slug"
      ></div>
    </div>
  </div>
</template>

<script lang="ts">
import { Context } from '@nuxt/types'
import type { $content } from '@nuxt/content'
import Vue from 'vue'

export default Vue.extend({
  mounted() {
    console.log(this.$content().fetch())
  },
  async asyncData(context: Context & { $content: typeof $content }) {
    const articles = await context.$content().fetch()

    return { articles }
  },
})
</script>

<style>
/* .container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
} */
</style>
