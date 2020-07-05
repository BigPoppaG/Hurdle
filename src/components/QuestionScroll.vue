<template>
  <div>
    <v-card>
      <v-container>
        <v-row><h3>Hurdle {{ currentQuestion + 1 }}</h3></v-row>  
        <v-row align="center">
          <v-col cols="2">
            <v-icon v-show="currentQuestion > 0" x-large @click="previousQuestion">mdi-chevron-left</v-icon>
          </v-col>
          <v-col cols="8" counter><question :key="currentQuestion" :question="questions[currentQuestion]" v-on:submitted="submitted" v-on:final="nextQuestion"/></v-col>
          <v-col cols="2">
            <v-icon v-show="currentQuestion < questions.length - 1" x-large @click="nextQuestion">mdi-chevron-right</v-icon>
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
          text: '2 + 5 = ?',
          answer: '7',
          submitted: null,
          cue: 'Answer',
          hint: {
            coreObjective: 'Addition up to ten',
            expectedLevel: 'This is a foundation skill that a lot of KS1 maths is built on. By KS1 children should know all the results of addition up to ten without calculation; so encourage your child to recite answers from memory before working it out.',
            suggestedPractice: 'Initially, children can learn to answer this type of question by counting fingers or counting the total number of objects in two sets.<br>It is never too early to ask word problems and relate these to the idea of addition and the + symbol. <i>eg. Molly has 5 sweets and Jack has 2 sweets, how many do they have all together?</i><br>',
            practiceQuestions: [
              {
                text: '7 + 2 = ?',
                answer: '9',
                submitted: null,
                cue: 'Answer'
              },
              {
                text: '3 + 5 = ?',
                answer: '8',
                submitted: null,
                cue: 'Answer'                
              },
            ]
          },
        },

        {
          text: 'What is the missing number: 17 + 4 = ?',
          answer: '21',
          submitted: null,
          cue: "Answer",
          hint: {
            coreObjective: 'Addition up to 100',
          }
        },
        {
          text: 'What is the missing number: ? - 17 = 20',
          image: '@\\public\favicon.ico',
          answer: '37',
          submitted: null,
          cue: "Answer",
        },
        {
          text: '\\framebox(200,300){} - 17 = 20',
          //hint: {},
        }          
      ],
      currentQuestion: 0,
    }
  },

  computed: {
    correct() {
      return this.questions[this.currentQuestion].submitted == this.questions[this.currentQuestion].answer
    },
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