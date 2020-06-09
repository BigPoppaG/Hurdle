<template>
  <div class="about">
    <h1>This is a question page</h1>
      <Question :question="questions[0]" />
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