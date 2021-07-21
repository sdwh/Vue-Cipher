<template>
  <h1>鍵泥棒のメソッド</h1>
  <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">HASH</router-link> |
    <router-link to="/about">Encrypt</router-link> |
    <router-link to="/about">Encode</router-link> |
    <a target="_blank" href="https://sdwh.dev">sdwh.dev</a>
  </div>
  <router-view/>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;
    margin-right: 20px;
    margin-left: 20px;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
