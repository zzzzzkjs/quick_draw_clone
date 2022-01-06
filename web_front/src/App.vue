<template>
  <div id="nav">
    <img alt="Vue logo" src="./assets/logo.png" id="vueLogo" />
    <router-link to="/">Home</router-link> |
    <router-link to="/canvas">Canvas</router-link>
    <button
      id="share_facebook"
      class="button button-facebook"
    ></button>
  </div>
  <router-view />
</template>

<style lang="scss">
body {
  margin: 0;
  padding: 0;
  display: initial;
  overflow: hidden;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

  position: absolute;
  min-width: 300px;
  min-height: 300px;
  width: 100%;
  height: 100%;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}

#vueLogo {
  position: absolute;
  left: 32px;
  top: 22px;
  height: 50px;
  width: 47px;
}

.button {
  position: absolute;
  right: 32px;
  top: 22px;
  display: inline-block;
  box-sizing: border-box;
  height: 50px;
  width: 47px;
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  padding-top: 0;
  padding-left: 6px;
  padding-right: 3px;
  padding-bottom: 18px;
  background-repeat: no-repeat;
  background-size: 94px 339px;
  background-position: 0 0;
  font-family: "Roboto Mono", sans-serif;
  font-weight: normal;
  font-size: 18px;
  text-align: center;
  color: #fff;
  cursor: pointer;
  overflow: hidden;
  -webkit-tap-highlight-color: rgba(255, 255, 255, 0);
  -webkit-tap-highlight-color: transparent;
  border: none;
}

.button-facebook {
  background-image: url(./assets/sprite.svg#buttons_small-usage);
  background-position: 0 -168px;
}

.button:active {
  background-position: -52px -168px;
}
</style>
