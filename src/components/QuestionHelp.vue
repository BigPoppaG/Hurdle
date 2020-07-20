<template>
  <div>
    <v-checkbox v-model="displayHelp" label="Need help?"></v-checkbox>
    <v-banner v-model="displayHelp" single-line transition="slide-y-transition">
      Placeholder for kid friendly help
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

    data() {
      return {
        displayHelp: true,
      }
    },
  }
</script>

<style>

</style>