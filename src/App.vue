<template>

  <div id="app">
    <v-app>
      <v-navigation-drawer app>
        <router-link to="/">Home</router-link> |
        <router-link to="/about">About</router-link>        
      </v-navigation-drawer>

      <v-app-bar app>
        <!-- -->
      </v-app-bar>

      <!-- Sizes your content based upon application components -->
      <v-content>

        <!-- Provides the application the proper gutter -->
        <v-container fluid>
          <router-view></router-view>
        </v-container>
      </v-content>

      <v-footer app>
        <!-- -->
      </v-footer>
    </v-app>
  </div>
</template>

<script>
export default {
  name: 'App',
  components: {
  },
  mounted() {
    let mathjaxScript = document.createElement('script')
    mathjaxScript.setAttribute('src', 'https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.2/MathJax.js?config=TeX-AMS_HTML')
    document.head.appendChild(mathjaxScript)
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
