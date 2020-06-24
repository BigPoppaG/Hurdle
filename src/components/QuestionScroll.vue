<template>
  <div>
    <v-card>
      <v-container>
        <v-row><h3>Hurdle {{ currentQuestion + 1 }}</h3></v-row>  
        <v-row align="center">
          <v-col cols="2">
            <v-icon x-large @click="previousQuestion">mdi-chevron-left</v-icon>
          </v-col>
          <v-col cols="8" counter><question :question="questions[currentQuestion]" v-on:submitted="submitted"/></v-col>
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
  name: 'QuestionScroll',
  components: {
    Question
  },

  data() {
    return {
      questions: [
        {
          text: 'What is the missing number: 17 + 4 = ?',
          answer: '21',
          submitted: '',
          cue: "Answer"
        },
        {
          text: 'What is the missing number: ? - 17 = 20',
          image: '@\\public\favicon.ico',
          answer: '37',
          submitted: '',
        },          
      ],
      currentQuestion: 0,
    }
  },

  methods: {
    nextQuestion() {
      this.currentQuestion = Math.min(this.currentQuestion+1, this.questions.length-1)
    },
    previousQuestion() {
      this.currentQuestion = Math.max(this.currentQuestion-1, 0)
    },
    submitted(newVal) {
      this.questions[this.currentQuestion].submitted = newVal
    },
  }

}
</script>

<style>

</style>