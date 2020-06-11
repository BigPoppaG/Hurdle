<template>
  <div class="question">
    <v-container>
      <v-row>
        <v-col cols="12"><vue-mathjax :formula="question.text"></vue-mathjax></v-col>
        <v-col cols="12"><img v-if: question.image v-bind:src="question.image"></v-col>
      
      </v-row>
    </v-container>
    
    <br>

    <div class="question-answer"><input @keyup.enter="submit" v-model="answer"></div>
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
    question: Object
  }, 
  data: function() { 
    return { 
      answer: ''
    } 
  }, 
  computed: { 
     
  }, 
  method: {
    submit: function() {
      //answer = 'test enter'
    }
  }

  //watch: { 
  //  answer: function (value, oldValue) { 
  //    return value + oldValue
  //   } 
  //},
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
