<template>
  <div class="question">
    <v-container>
      <v-row align-text-left>
        <v-col cols="12"><vue-mathjax :formula="question.text" :options="{chtml: {displayAlign: 'left'}}"></vue-mathjax></v-col>
        <v-col cols="12" v-if=showImage ><img class="question-image" :src="question.image.src" :height="question.image.height" :width="question.image.width"></v-col>
        <v-col cols="12" class="question-answer">
          <v-text-field 
            v-model="submitted"
            :label="question.cue" 
            outlined 
            :autofocus="primary"
            autocomplete="off"
            :clearable="!correct"
            :success="correct"
            :error="showError"            
            @keyup.enter="submit"
            :append-icon="correct ? 'mdi-check-bold' : 'mdi-pencil'">
          </v-text-field>

          <question-hint v-if: showHint :hint="question.hint" :submitted="question.submitted"></question-hint>
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
    question: Object,
    primary: Boolean,
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
      return "hint" in this.question
    },  
    showImage: function() {
      return "image" in this.question
    },      
    showError: function() {
      return false && !this.correct && !(this.submitted == null || this.submitted == '')
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
  .question-image {  width: 100%;  height: auto; }
</style>
