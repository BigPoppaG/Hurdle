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
        <div v-if='"coreObjective" in hint'>
        <v-card-title
            class="headline grey lighten-2"
            primary-title
        >
            Core Objective
        </v-card-title>

        <v-card-text class="text-sm-left">
            {{ hint.coreObjective }}
        </v-card-text>
        </div>

        <v-divider></v-divider>

        <div v-if='"expectedLevel" in hint'>
        <v-card-title
            class="headline grey lighten-2"
            primary-title
        >
            Expected Level
        </v-card-title>

        <v-card-text class="text-sm-left">
            {{ hint.expectedLevel }}
        </v-card-text>
        </div>

        <v-divider></v-divider>

        <div v-if='"suggestedPractice" in hint'>
        <v-card-title
            class="headline grey lighten-2"
            primary-title
        >
            Suggested Practice
        </v-card-title>

        <v-card-text class="text-sm-left">
            {{ hint.suggestedPractice }}
        </v-card-text>
        </div>

        <v-divider></v-divider>

        <div v-if='"practiceQuestions" in hint'>
        <v-card-title
            class="headline grey lighten-2"
            primary-title
        >
            Practice Questions
        </v-card-title>

        <v-card-text class="text-sm-left">
            <question v-for="question in hint.practiceQuestions" :key="question.id" :question="question"/>
        </v-card-text>
        </div>

        <v-divider></v-divider>

        <div v-if='"videoLinks" in hint'>
        <v-card-title
            class="headline grey lighten-2"
            primary-title
        >
            Online Videos
        </v-card-title>

        <v-card-text class="text-sm-left">
            <v-list>
                <v-list-item
                v-for="link in hint.videoLinks" 
                :key="link.id" 
                >
                    <iframe 
                    :src="link + '? autoplay=0&rel=0'"
                    width="560" 
                    height="315"
                    frameborder="0" 
                    allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" 
                    allowfullscreen
                    >
                    Video Unavalable
                    </iframe>
                </v-list-item>
            </v-list>    
        </v-card-text>
        </div>

        <v-divider></v-divider>

        <div v-if='"learningResources" in hint'>
        <v-card-title
            class="headline grey lighten-2"
            primary-title
        >
            Learning Resources
        </v-card-title>

        <v-card-text class="text-sm-left">
            <v-list>
                <v-list-item
                v-for="resource in hint.learningResources" 
                :key="resource.id" 
                >
                <v-list-item-content>
                    <v-list-item-title>
                       <a :href="resource.link" target="_blank">{{resource.description}}</a>
                    </v-list-item-title>
                </v-list-item-content>
                </v-list-item>
            </v-list>
        </v-card-text>
        </div>

        <v-divider></v-divider>

        <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn
            color="primary"
            text
            @click="dialog = false"
            >
            OK
            </v-btn>
        </v-card-actions>
        </v-card>
    </v-dialog>
</template>

<script>
export default {
    name: 'QuestionHint',
    components: {
      Question: () => import('../components/Question.vue')  //Needed for recursive components
    },
    props: {
      hint: Object,  
    },
    data () {
      return {
        dialog: false,
      }
    },
    computed: {
      hasCoreObjective() {
        return "coreObjective" in this.hint  
      }
    }
}
</script>

<style>

</style>