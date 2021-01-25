<template>
  <h1>期末作品呈現</h1>
  <p>
    老師我本來想要做一個自己的網站，但是我失敗了。
  </p>
  <p>
    所以就玩一些P5，但我還是會把我自己網站的半成品附上。
  </p>
  <div id="nav">
    <router-link to="/">無題之一</router-link> |
    <router-link to="/example2">無題之二</router-link> |
    <router-link to="/example3">無題之三</router-link> |
    <router-link to="/example4">無題之四</router-link>
  </div>
  <router-view :key="$route.fullPath"/>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
