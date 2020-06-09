<template>
  <div class="about">
    <h1>This is a question page</h1>
      <question-scroll/>
  </div>
</template>


<script>
import QuestionScroll from '../components/QuestionScroll.vue'

export default {
  name: 'App',
  components: {
    QuestionScroll
  }
}
</script>