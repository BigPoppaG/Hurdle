<template>
  <div>
    <v-card>
      <v-container>
        <v-row>Question {{ 1 }}</v-row>  
        <v-row align="center">
          <v-col cols="2">
            <v-icon x-large @click="previousQuestion">mdi-chevron-left</v-icon>
          </v-col>
          <v-col cols="8"><question :question="questions[currentQuestion]"/></v-col>
          <v-col cols="2">
            <v-icon x-large @click="nextQuestion">mdi-chevron-right</v-icon>
          </v-col>
        </v-row>
      </v-container>
    </v-card>
  </div>
</template>

<script>
import Question from '../components/Question.vue'

export default {
  name: 'App',
  components: {
    Question
  },

  data() {
    return {
      questions: [
        {
          text: 'if (ax^2 +bx+c = 0) then $$x = {-b \\pm \\sqrt{b^2-4ac} \\over 2a}$$',
          image: '',
          answer: ''
        },
        {
          text: 'question 2 what is 3+4?',
          image: '@\\public\favicon.ico',
          answer: ''
        },          
      ],
      currentQuestion: 0,
    }
  },

  methods: {
    nextQuestion() {
      this.currentQuestion = Math.min(this.currentQuestion+1, this.questions.length)
    },
    previousQuestion() {
      this.currentQuestion = Math.max(this.currentQuestion-1, 0)
    },    
  }

}
</script>

<style>

</style>