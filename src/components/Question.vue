<template>
  <div class="question">
    <div class="qestion-number">{{ number }}</div>  
    <textarea v-model="formula" cols="30" rows="10"></textarea>
    <vue-mathjax :formula="formula"></vue-mathjax>
    <div class="question-text">{{ text }}</div>
    <div class="question-answer"><input v-model="answer" ></div>
  </div>
</template>

<script>
import { VueMathjax } from 'vue-mathjax'
export default {
  name: 'Question',
  components: {
    'vue-mathjax': VueMathjax
  },
  props: { 
    number: Number, 
    text: String
  }, 
  data: function() { 
    return { 
      answer: '',
      formula: 'if (ax^2 +bx+c = 0) then $$x = {-b \\pm \\sqrt{b^2-4ac} \\over 2a}.$$'
    } 
  }, 
  computed: { 
     
  }, 
  
  //watch: { 
  //  answer: function (value, oldValue) { 
  //    return value + oldValue
  //   } 
  //},
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
