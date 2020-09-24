<template>
  <div id="lore-app">
    <header>
      <div class="header-center">
        <div class="logo">
          <nuxt-link to="/">
            <img src="~assets/zenerith.png" />
          </nuxt-link>
        </div>
        <div id="main-nav"></div>
      </div>
    </header>
    <main><Nuxt /></main>
    <footer>
      <pane class="footer">
        <div class="footer-columns">
          <div></div>
          <div class="align-right">
            <p>
              Site design and logos &copy;
              <a href="https://vorlias.com">Jonathan Holmes</a>, 2020
            </p>
            <p>
              Contribute on
              <a href="https://github.com/roblox-aurora/lore.zenerith.com"
                >GitHub</a
              >
            </p>
          </div>
        </div>
      </pane>
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
  margin: 10px;
  border-radius: 5px;

  .header-center {
    margin: 0 auto;
    max-width: 1500px;
    display: flex;
    justify-content: space-between;

    .logo {
      padding-left: 15px;
      padding-right: 15px;
    }
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

footer {
  .footer-columns {
    color: white;

    a {
      color: #d8d8d8;
      text-decoration: none;
    }

    .align-right {
      text-align: right;
    }

    max-width: 1500px;
    margin: 10px auto;
    display: grid;
    grid-template-columns: 50% 50%;
  }
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

// *,
// *::before,
// *::after {
//   box-sizing: border-box;
//   margin: 0;
// }

#main-nav {
  margin: 8px;
  display: flex;
}

article {
  max-width: 1500px;
  margin: 15px auto;
  color: white;

  *,
  *::before,
  *::after {
    box-sizing: border-box;
    margin: 2px;
  }

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
        color: #b0b0b0;
        text-decoration: none;
        font-size: 20px;

        &.nuxt-link-exact-active {
          color: #f8f8f8;
        }
      }
    }
  }

  h1 {
    font-size: 30px;

    &.title {
      font-size: 30px;
    }
  }

  h2 {
    font-size: 22px;
  }

  p {
    padding: 5px;
  }
}
</style>
