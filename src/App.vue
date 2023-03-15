<script >
import Steppers from './components/Steppers.vue';
import Quiz from './components/Quiz.vue';
import Roles from './components/Roles.vue';
import Result from './components/result.vue';

export default {
  components: {
    Steppers,
    Quiz,Roles,Result
  },
  data(){
    return {
      cureentComp:Roles,
      score: 0,
      currentStep:1,

    questions : [
        {
          question: 'What is the "v-bind" directive used for in Vue.js?',
          choices: [
            'To bind a JavaScript expression to a DOM element',
            'To define a method on a Vue instance',
            'To define a computed property on a Vue instance',
            'To define a data property on a Vue instance'
          ],
          correct: 0,
          passed: false
        },
        {
          question: 'What is the purpose of the "v-model" directive in Vue.js?',
          choices: [
            'To bind a JavaScript expression to a DOM element',
            'To define a method on a Vue instance',
            'To define a computed property on a Vue instance',
            'To bind form input values to a Vue instance data property'
          ],
          correct: 3,
          passed: false
        },
        {
          question: 'What is the Vue.js lifecycle hook that is called when a component is created?',
          choices: [
            'created',
            'mounted',
            'updated',
            'destroyed'
          ],
          correct: 0,
          passed: false
        },
        {
          question: 'What is the difference between "v-if" and "v-show" in Vue.js?',
          choices: [
            '"v-if" only renders the element if the condition is true, while "v-show" toggles the "display" CSS property',
            '"v-show" only renders the element if the condition is true, while "v-if" toggles the "display" CSS property',
            'There is no difference between "v-if" and "v-show"',
            'Both "v-if" and "v-show" toggle the "display" CSS property'
          ],
          correct: 0,
          passed: false
        },
        {
          question: 'What is the Vue.js directive used to bind to an event?',
          choices: [
            'v-bind',
            'v-model',
            'v-on',
            'v-show'
          ],
          correct: 2,
          passed: false
        },
        {
          question: 'What is the Vue.js component lifecycle hook that is called when a component is destroyed?',
          choices: [
            'created',
            'mounted',
            'updated',
            'destroyed'
          ],
          correct: 3,
          passed: false
        },
        {
          question: 'What is the Vue.js directive used to repeat elements in a list?',
          choices: [
            'v-repeat',
            'v-bind',
            'v-for',
            'v-show'
          ],
          correct: 2,
          passed: false
        },
        {
          question: 'What is the Vue.js feature that allows a parent component to pass data to a child component?',
          choices: [
            'Props',
            'Data',
            'Methods',
            'Computed properties'
          ],
          correct: 0,
          passed: false
        },
        {
          question: 'What is the Vue.js method used to fetch data from an API?',
          choices: [
            'fetch()',
            'get()',
            'post()',
            'axios()'
          ],
          correct: 3,
          passed: false
        },
        {
          question: 'What is the Vue.js feature that allows a component to have its own internal state?',
          choices: [
            'Props',
            'Data',
            'Methods',
            'Computed properties'
          ],
          correct: 1,
          passed: false
        },
        {
          question: 'What is the Vue.js directive used to bind an attribute to a dynamic value?',
          choices: [
            'v-bind',
            'v-model',
            'v-on',
            'v-show'
          ],
          correct: 0,
          passed: false
        }
      ],

      currentQuestion: '1',
    }
  },
  methods:{

    show_result(score){
      this.cureentComp = Result
      this.score = score
      this.currentStep=3

    },
    startQuiz(){
      this.cureentComp = Quiz
      this.currentStep=2

    }
  }

}
</script>

<template>
  <header>
    <div class="row">
          <div class="block border" >
            <Steppers :currentStep="currentStep"></Steppers>
          </div>
    </div>
  </header>
  <main >
    <div class="row ">
      <div class="block border " style="min-height: 70vh;">
        <component :is="cureentComp" @start-quiz="startQuiz" :questions="questions" @return_result="show_result" :score="score"> </component>
      </div>
   </div>
  </main>




 
</template>

<style scoped>

</style>
