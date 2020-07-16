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
          text: '9 - 6 = ?',
          answer: '3',
          submitted: null,
          cue: "Answer",
          hint: {
            coreObjective: 'Subtraction with single digits',
            suggestedPractice: 'This type of question can be approached initially by counting from the starting number, or by removing items from an initial set and counting how many remain. Relate the question to word problems; eg. if Molly has 9 sweets and eats six of them how many does she have left? Also relate the question to the corresponding addition question: ? + 6 = 9. Use the students recall of the results of addition to help learn the results of these single digit subtractions. Eventually all single digit subtractions should be known from memory.',
            practiceQuestions: [
              {
                text: 'What number do you need to add to six to get nine?',
                answer: '3',
                submitted: null,
                cue: 'Answer',
              },
              {
                text: 'Jack had 9 pounds but spent 5 pounds on a new toy. How any pounds does he have left?',
                answer: '4',
                submitted: null,
                cue: 'Answer',
              },
              {
                text: '7 - 2 = ?',
                answer: '5',
                submitted: null,
                cue: 'Answer',
              },
              {
                text: '8 - 3 = ?',
                answer: '5',
                submitted: null,
                cue: 'Answer',         
              },
            ]
          },
        },

        {
          text: '22 + 6 = ?',
          answer: '28',
          submitted: null,
          cue: "Answer",
          hint: {
            coreObjective: 'Addition without crossing a ten',
            suggestedPractice: 'Think about partitioning numbers into tens and units. In this question 22 can be thought of as two tens and two units. So the question can be seen to be similar to 2 + 6 but with an extra two tens.',
            practiceQuestions: [
              {
                text: '17 + 2 = ?',
                answer: '19',
                submitted: null,
                cue: 'Answer',
              },
              {
                text: '30 + 8 = ?',
                answer: '38',
                submitted: null,
                cue: 'Answer',         
              },
            ]
          },
        },


        {
          text: '18 - 6 = ?',
          answer: '12',
          submitted: null,
          cue: "Answer",
            hint: {
            coreObjective: 'Subtracting without crossing a ten',
            suggestedPractice: "Think about partitioning numbers into tens and units. In this question 18 can be thought of as one ten and eight units. So the question can be seen to be similar to 8 - 2 but with an extra ten.",
            practiceQuestions: [
              {
                text: '27 - 4 = ?',
                answer: '23',
                submitted: null,
                cue: 'Answer',
              },
              {
                text: '19 - 5 = ?',
                answer: '14',
                submitted: null,
                cue: 'Answer',         
              },
            ]
          },
        },

        {
          text: '23 + 30 = ?',
          answer: '53',
          submitted: null,
          cue: "Answer",
            hint: {
            coreObjective: 'Adding with tens and units',
            suggestedPractice: "Think about partitioning numbers into tens and units. In this question 23 can be thought of as 2 tens and 3 units, while 30 is 3 tens and no units. So in total we have 5 tens and 3 units, which we write as 53 and call fifty three. In this way the two digit addition question is split into two single digit addition questions. Make sure the single digit additions can be done quickly from recall, and if not go back and practice those.",
            practiceQuestions: [
              {
                text: '16 + 13 = ?',
                answer: '29',
                submitted: null,
                cue: 'Answer',
              },
              {
                text: '20 + 17 = ?',
                answer: '37',
                submitted: null,
                cue: 'Answer',
              },
            ]
          },
        },

        {
          text: '47 - 12 = ?',
          answer: '35',
          submitted: null,
          cue: "Answer",
            hint: {
            coreObjective: 'Subtracting with tens and units',
            suggestedPractice: "Think about partitioning numbers into tens and units. In this question 47 can be thought of as 4 tens and 7 units, while 12 is 1 ten and 2 unit. So the difference is 3 tens and 5 units, which we write as 35 and call thirty five. In this way the two digit subtraction question is split into two single digit subtraction questions. Make sure the single digit subtractions can be done quickly from recall, and if not go back and practice those.",
            practiceQuestions: [
              {
                text: '64 - 20 = ?',
                answer: '44',
                submitted: null,
                cue: 'Answer',
              },
              {
                text: '19 - 15 = ?',
                answer: '4',
                submitted: null,
                cue: 'Answer',
              },
            ]
          },
        },

        {
          text: '7 + 3 + 2 = ?',
          answer: '12',
          submitted: null,
          cue: "Answer",
            hint: {
            coreObjective: 'Adding multiple numbers',
            suggestedPractice: "The key idea here is that you can add numbers in pairs and not care about the order. So 5 + 10 + 6 = 15 + 6 = 21. To see why this works you can use the idea of counting the total number of items in multiple groups and seeing that it doesn't matter what order you put the groups together.",
            practiceQuestions: [
              {
                text: '8 + 2 + 7 = ?',
                answer: '17',
                submitted: null,
                cue: 'Answer'
              },
              {
                text: '15 + 5 + 3 = ?',
                answer: '23',
                submitted: null,
                cue: 'Answer',          
              },
            ]
          },
        },


        {
          text: '65 + 9 = ?',
          answer: '74',
          submitted: null,
          cue: "Answer",
            hint: {
            coreObjective: 'Adding with tens and units, crossing a ten',
            suggestedPractice: "When the total number of units in a sum is greater than ten we need to represent the extra tens in the tens column, and add these to the tens we already have in the sum. This could be thought of as trading up ten units into one ten. In this question the 65 has 5 units already so when we add on the extra 9 units we get a total of 14 units. We can then partition this 14 into 1 ten and 4 units. The 65 in the question already had 6 tens, so the extra ten we get from the sum of the units gives us 7 tens in total, with 4 extra units. We write this as 74 and call it seventy four. An alternative approach is to 'use up' 5 out of the 9 units to bring the 65 up to 70 (65 + 5), which leaves us with 4 extra units (9 - 5). This approach may be more natural for children who have been practicing number bonds to ten and so can quickly spot the number of units needed to get up to the next ten. Another approach that works well in this example is to ask first the different question 65 + 10. This is easily seen to be 75 by counting tens and units. The answer to the real question is 1 less than this because we are only adding 9 instead of 10, so the real answer must be 74. Encourage a range of apporaches and encourage the student to explain their apporach.",
            practiceQuestions: [
              {
                text: '60 + 14 = ?',
                answer: '74',
                submitted: null,
                cue: 'Answer',
                hint:{
                  suggestedPractice: "This is how you could simplify the original question using the first approach of first combining the 5 units from the 65 and the 9 units to get 14 units."
                }
              },
              {
                text: '65 + 5 + 4 = ?',
                answer: '74',
                submitted: null,
                cue: 'Answer',
                hint:{
                  suggestedPractice: "This is how you could simplify the original question using the second approach of first splitting the 9 units up into the 5 you need to get to the next ten, and an extra 4 left over."
                }
              },
              {
                text: '65 + 10 - 1 = ?',
                answer: '74',
                submitted: null,
                cue: 'Answer',
                hint:{
                  suggestedPractice: "This is how you could simplify the original question using the third approach of first thinking of the simpler question of 65 + 10, and then subtracting one from the answer to reflect the fact that we only want to add on 9 instead of 10."
                }
              },
              {
                text: '27 + 6 = ?',
                answer: '33',
                submitted: null,
                cue: 'Answer',
                hint:{
                  suggestedPractice: "Try using one or more of the above techniques to answer this question and see that they give you the same answer."
                }
              },
            ]
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
          text: '\\framebox(200,300){} - 17 = 20',
        }, 
      
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