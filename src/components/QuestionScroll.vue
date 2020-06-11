<template>
  <div>
    <v-card>
      <h2>Question {{ 1 }}</h2>
      <v-container>
        <v-row>
          <v-col cols="2">
            <v-icon mdi-chevron_left>left</v-icon>
          </v-col>
          <v-col cols="8"><question :question="questions[0]"/></v-col>
          <v-col allign-self="centre" cols="2">
            <v-icon mdi-chevron_right>right</v-icon>
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

</style>