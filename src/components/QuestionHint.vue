<template>
    <v-dialog
        v-model="dialog"
    >
        <template v-slot:activator="{ on, attrs }">
        <v-btn 
            color="red lighten-2"
            dark
            v-bind="attrs"
            v-on="on"
        >
            Get Help
        </v-btn>
        </template>

        <v-card>
        <v-card-title
            class="headline grey lighten-2"
            primary-title
        >
            Core Objective
        </v-card-title>

        <v-card-text>
            {{ hint.coreObjective }}
        </v-card-text>

        <v-divider></v-divider>

        <v-card-title
            class="headline grey lighten-2"
            primary-title
        >
            Expected Level
        </v-card-title>

        <v-card-text>
            {{ hint.expectedLevel }}
        </v-card-text>

        <v-divider></v-divider>

        <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn
            color="primary"
            text
            @click="dialog = false"
            >
            I accept
            </v-btn>
        </v-card-actions>
        </v-card>
    </v-dialog>
</template>

<script>
export default {
    name: 'QuestionHint',
    props: {
      hint: Object,  
    },
    data () {
      return {
        dialog: false,
      }
    },

}
</script>

<style>

</style>