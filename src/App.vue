<template>
  <h1>鍵泥棒のメソッド</h1>
  <div id="nav">
    <router-link to="/">Home</router-link> <span class="vertical-line">|</span>
    <router-link to="/aes">AES</router-link> <span class="vertical-line">|</span>
    <a target="_blank" href="https://sdwh.dev">sdwh.dev</a>
  </div>
  <router-view/>
</template>

<style scoped>
.vertical-line{
  font-weight: 900;
  color: darksalmon;
}
</style>

<style lang="scss">
h1 {
  display: block;
  font-size: 2em;
  margin-block-start: 0.67em;
  margin-block-end: 0.67em;
  margin-inline-start: 0px;
  margin-inline-end: 0px;
  font-weight: bold;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  a {
    font-size: 1.5rem;
    font-weight: bold;
    color: #2c3e50;
    margin-right: 10px;
    margin-left: 10px;
    padding: 0;
    text-decoration: none;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
