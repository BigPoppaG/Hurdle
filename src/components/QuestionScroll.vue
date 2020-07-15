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
            suggestedPractice: 'Initially, children can learn to answer this type of question by counting fingers, counting the total number of objects in two sets, or by counting on from one of the numbers. It is good to combine this type of question with word problems and relate these to the idea of addition and the + symbol; eg. Molly has 5 sweets and Jack has 2 sweets, how many do they have all together? By Year 2, however, children should be able to recall all of the additions up to ten quickly from memory without any counting on. This should be practiced until all pairs of numbers up to ten can be recalled easily.',
            practiceQuestions: [
              {
                text: '7 + 2 = ?',
                answer: '9',
                submitted: null,
                cue: 'Answer',
              },
              {
                text: '3 + 5 = ?',
                answer: '8',
                submitted: null,
                cue: 'Answer',
              },
            ],
            videoLinks: [
              'https://www.youtube.com/embed/Vti8Iivvgag',
            ],
            learningResources: [
              {
                description: 'A nice game for practicing addition up to 20',
                link: 'https://www.topmarks.co.uk/addition/robot-addition'    
              },
            ],
            commonErrors: {
              '25': {
                description: 'When you add two numbers it is',
                image: '',
                videoLinks: []
              }  
            }
          },
        },
        {
          text: '2 + 5 = ?',
          answer: '7',
          submitted: null,
          cue: 'Answer',
          hint: {
            coreObjective: 'Addition up to ten',
            expectedLevel: 'This is a foundation skill that a lot of KS1 maths is built on. By KS1 you should know all the results of addition up to ten without calculation. Try to recall the answer from memory before working it out.',
            suggestedPractice: 'Initially, children can learn to answer this type of question by counting fingers or counting the total number of objects in two sets.<br>It is never too early to ask word problems and relate these to the idea of addition and the + symbol. <i>eg. Molly has 5 sweets and Jack has 2 sweets, how many do they have all together?</i><br>',
            practiceQuestions: [
              {
                text: '7 + 2 = ?',
                answer: '9',
                submitted: null,
                cue: 'Answer',
              },
              {
                text: '3 + 5 = ?',
                answer: '8',
                submitted: null,
                cue: 'Answer',
              },
            ],
            videoLinks: [
              'https://www.youtube.com/embed/Vti8Iivvgag',
            ],
            commonErrors: {
              '25': {
                description: '',
                image: '',
                videoLinks: []
              }  
            }
          },
        },
        {
          text: 'What is the total value of these coins?',
          image: 'public\\Year 2\\Coins.png',
          answer: ['57', '57p', '57 pence'],
          submitted: null,
          cue: 'Answer',
          hint: {
            coreObjective: 'Compose a two digit number by counting tens and units',
            expectedLevel: 'This is a foundation skill that a lot of KS1 maths is built on. By KS1 you should know all the results of addition up to ten without calculation. Try to recall the answer from memory before working it out.',
            suggestedPractice: 'Initially, children can learn to answer this type of question by counting fingers or counting the total number of objects in two sets.<br>It is never too early to ask word problems and relate these to the idea of addition and the + symbol. <i>eg. Molly has 5 sweets and Jack has 2 sweets, how many do they have all together?</i><br>',
            practiceQuestions: [
              {
                text: '7 + 2 = ?',
                answer: '9',
                submitted: null,
                cue: 'Answer',
              },
              {
                text: '3 + 5 = ?',
                answer: '8',
                submitted: null,
                cue: 'Answer',
              },
            ],
            videoLinks: [
              'https://www.youtube.com/embed/Vti8Iivvgag',
            ],
            commonErrors: {
              '25': {
                description: '',
                image: '',
                videoLinks: []
              }  
            }
          },
        },

        {
          text: '9 - 6 = ?',
          answer: '3',
          submitted: null,
          cue: "Answer",
          hint: {
            coreObjective: 'Subtraction with single digits',
            expectedLevel: 'This is a foundation skill that a lot of KS1 maths is built on. By KS1 you should know all the results of addition up to ten without calculation; so encourage your child to recite answers from memory before working it out.',
            suggestedPractice: 'Initially, children can learn to answer this type of question by counting fingers or counting the total number of objects in two sets.<br>It is never too early to ask word problems and relate these to the idea of addition and the + symbol. <i>eg. Molly has 5 sweets and Jack has 2 sweets, how many do they have all together?</i><br>',
            practiceQuestions: [
              {
                text: '7 - 2 = ?',
                answer: '5',
                submitted: null,
                cue: 'Answer',
                hint:{}
              },
              {
                text: '8 - 3 = ?',
                answer: '5',
                submitted: null,
                cue: 'Answer',
                hint:{}                
              },
            ]
          },
        },
        {
          text: '5 + 10 + 6 = ?',
          answer: '21',
          submitted: null,
          cue: "Answer",
            hint: {
            coreObjective: 'Adding multiple numbers',
            suggestedPractice: "The key idea here is that you can add numbers in pairs and not care about the order. So 5 + 10 + 6 = 15 + 6 = 21. To see why this works you can use the idea of counting the total number of items in multiple groups and seeing that it doesn't matter what order you put the groups together.",
            practiceQuestions: [
              {
                text: '8 + 3 + 7 = ?',
                answer: '18',
                submitted: null,
                cue: 'Answer',
                hint:{}
              },
              {
                text: '15 + 7 + 5 = ?',
                answer: '27',
                submitted: null,
                cue: 'Answer',
                hint:{}                
              },
            ]
          },
        },
        {
          text: '\\framebox(200,300){} - 17 = 20',
        }, 
        {
      text: 'Complete the sentences: 500 made 1,000 times the size is ...',
      answer: '500000',
      submitted: null,
      cue: 'Answer',
      hint: {
        coreObjective: 'Understand the relationship between powers of 10 from 1 hundredth to 10 million, and use this to make a given number 10, 100, 1,000, 1 tenth, 1 hundredth or 1 thousandth times the size (multiply and divide by 10, 100 and 1,000).',
        //expectedLevel: '',
        suggestedPractice: '',
        practiceQuestions: [
          {
            text: '7 + 2 = ?',
            answer: '9',
            submitted: null,
            cue: 'Answer',
          },
          {
            text: '3 + 5 = ?',
            answer: '8',
            submitted: null,
            cue: 'Answer',
     
          },
        ],
        videoLinks: [
          'https://www.youtube.com/embed/Vti8Iivvgag',
        ]
      },
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