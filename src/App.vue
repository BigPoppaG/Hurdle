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
    <Question :question="questions[0]" />
    <br/>
    <QuestionEdit />

  </div>
</template>

<script>
import Question from './components/Question.vue'
import QuestionEdit from './components/QuestionEdit.vue'

export default {
  name: 'App',
  components: {
    Question,
    QuestionEdit
  },
  mounted() {
    let mathjaxScript = document.createElement('script')
    mathjaxScript.setAttribute('src', 'https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.2/MathJax.js?config=TeX-AMS_HTML')
    document.head.appendChild(mathjaxScript)
  },
  data() {
    return {
      questions: [
          {
            text: 'if (ax^2 +bx+c = 0) then $$x = {-b \\pm \\sqrt{b^2-4ac} \\over 2a}$$',
            image: ''
          },
          {
            text: 'if (ax^2 +bx+c = 0) then $$x = {-b \\pm \\sqrt{b^2-4ac} \\over 2a}$$',
            image: ''
          },          
        ]
    }
  }
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
