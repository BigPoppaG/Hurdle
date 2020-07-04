<template>
  <div class="question">
    <v-container>
      <v-row align-text-left>
        <v-col cols="12"><vue-mathjax :formula="question.text" :options="{chtml: {displayAlign: 'left'}}"></vue-mathjax></v-col>
        <v-col cols="12"><img v-if: question.image v-bind:src="question.image"></v-col>
        <v-col cols="12" class="question-answer">
          <v-text-field 
            v-model="submitted"
            :label="question.cue" 
            outlined 
            autofocus
            :clearable="!correct"
            :success="correct"
            :error="!correct && !(this.submitted == null || this.submitted == '')"            
            @keyup.enter="submit"
            :append-icon="correct ? 'mdi-check-bold' : unspecified">
          </v-text-field>
          <v-divider></v-divider>
          <question-hint v-if: showHint :hint="question.hint"></question-hint>
        </v-col>      
      </v-row>
    </v-container>
  </div>
</template>

<script>
import { VueMathjax } from 'vue-mathjax'
import QuestionHint from '../components/QuestionHint.vue'
export default {
  name: 'Question',
  components: {
    'vue-mathjax': VueMathjax,
    'question-hint': QuestionHint
  },
  props: { 
    question: Object
  }, 
  data: function() { 
    return { 
      submitted: this.question.submitted
    } 
  }, 
  computed: { 
    correct: function() {
      return this.question.answer == this.submitted
    },
    showHint: function() {
      return this.question.hint
    },  
  }, 
  methods: {
    submit() {
      this.$emit('final')
    }
  },
  watch: {
    submitted() { 
      this.$emit('submitted', this.submitted)
    },
    question() {
      this.submitted = this.question.submitted
    }, 
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  /deep/.v-input__icon--append .v-icon { 
      color: green;
  }
</style>
