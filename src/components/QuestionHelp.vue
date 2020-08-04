<template>
  <div>
    <v-btn class="help-btn" v-show="!displayHelp"  left @click.prevent="displayHelp = !displayHelp"><v-icon right x-large color=blue>mdi-account-question</v-icon></v-btn>
    <div v-show=false><v-checkbox label=""></v-checkbox></div>
    <v-banner v-model="displayHelp" single-line transition="slide-y-transition">
      text
      <template v-slot:actions="{ dismiss }">
        <v-btn text color="primary" @click="dismiss">OK</v-btn>
        <v-btn text color="primary">Still stuck</v-btn>
      </template>
    </v-banner>
  </div>
</template>

<script>
  export default {
    name: 'QuestionHelp',
    props: {
      help: Object
    },
    data() {
      return {
        displayHelp: false,
      }
    },
  }
</script>

<style scoped>

    .help-btn {
        float: left;
    }

</style>