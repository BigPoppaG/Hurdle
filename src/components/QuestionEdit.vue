<template>
  <div class="question">
    <textarea v-model="formula" cols="30" rows="10"></textarea>
    <br/>
    <vue-mathjax :formula="formula"></vue-mathjax>
    <img v-bind:src="image">
  </div>
</template>

<script>
import { VueMathjax } from 'vue-mathjax'
export default {
  name: 'QuestionEdit',
  components: {
    'vue-mathjax': VueMathjax
  },
  data() { 
    return { 
      formula: 'if (ax^2 +bx+c = 0) then $$x = {-b \\pm \\sqrt{b^2-4ac} \\over 2a}.$$',
      image: ''
    } 
  }, 

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
