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

.button--green {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #3b8070;
  color: #3b8070;
  text-decoration: none;
  padding: 10px 30px;
}

.button--green:hover {
  color: #fff;
  background-color: #3b8070;
}

.button--grey {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #35495e;
  color: #35495e;
  text-decoration: none;
  padding: 10px 30px;
  margin-left: 15px;
}

.button--grey:hover {
  color: #fff;
  background-color: #35495e;
}
</style>
