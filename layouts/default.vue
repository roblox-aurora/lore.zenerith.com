<template>
  <div id="lore-app">
    <header>
      <div class="header-center">
        <div class="logo">
          <nuxt-link to="/">
            <img src="~assets/zenerith.png" />
          </nuxt-link>
        </div>
      </div>
    </header>
    <main><Nuxt /></main>
    <footer>
      <pane class="footer"> </pane>
    </footer>
  </div>
</template>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Balthazar&display=swap');

header {
  height: 80px;

  background-image: url('~assets/muddyslate.jpg');
  border: 1px solid #51473d;
  padding-top: 5px;

  .header-center {
    margin: 0 auto;
    max-width: 1500px;
    display: flex;
    justify-content: space-between;
  }
}

main {
  min-height: calc(100vh - 95px);
}

body {
  margin: 0px;
  padding: 0px;
  background-image: url('~assets/darkslate.jpg');
}

html {
  font-family: 'Balthazar', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}

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
