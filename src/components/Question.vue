<template>
  <div class="question">
    <div class="qestion-number">{{ number }}</div>  
    <div class="question-text">{{ text }}</div>
    <div class="question-answer"><input v-model="answer" ></div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: { 
    number: Number, 
    text: String, 
  }, 
  data: function() { 
    return { 
      answer: ''    
    } 
  }, 
  computed: { 
     
  }, 
  
  watch: { 
    answer: function (value, oldValue) { 
      return value + oldValue
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
