<script>
export default {
    props:[
        'questions',
    ],
    data(){
        return {
            isCorrect :false,
            currentQuestion : 0,
            choice_color: 'bg-white',
            option_selected: false,
            score:0,
            completed:false
        }
    },
    methods: {
        getAnswer(index){
            this.option_selected=index
            if (this.option_selected == this.questions[this.currentQuestion].correct) {
                   this.score++;
            }

        },
       getChoiceClass(index) {
       if (this.option_selected === index) {
        if (index === this.questions[this.currentQuestion].correct) {
          return "bg-success";
        } else {
          return "bg-danger";
        }
      } else {
        return "bg-white";
       }
      },
      newQuestion(){
        if(this.currentQuestion+1!=this.questions.length) {
        this.option_selected=false;
        this.currentQuestion++;
        }
        else{
            this.completed=true;
        }
      }
    }
   
  }

</script>
<template>
    <div class="quiz">
      <div class="question">{{ questions[currentQuestion].question }}</div>
      <div class="choices">
        <div v-for="(choice,index) in questions[currentQuestion].choices" 
             :key="index"
             :class="[getChoiceClass(index), 'choice']"
             @click="getAnswer(index)"
             :disabled="option_selected !== false"
             >
          {{ choice }}
        </div>
      </div>
      <button v-if="!completed" 
              class="next-btn"
              :class="{ disabled: option_selected === false }"
              :disabled="option_selected === false"
              @click="newQuestion"
              >
        Next
      </button>
      <button v-else 
              class="view-result-btn"
              @click="$emit('return_result',score)">
        View Result
      </button>
    </div>
  </template>
  
  <style scoped>
  .quiz {
    margin: 2em auto;
    max-width: 600px;
    text-align: center;
  }
  
  .question {
    font-size: 1.5em;
    font-weight: bold;
    margin-bottom: 1em;
  }
  
  .choices {
    display: flex;
    flex-direction: column;
  }
  
  .choice {
    margin: 1em auto;
    padding: 1em;
    border: 2px solid #000;
    border-radius: 0.5em;
    cursor: pointer;
    transition: background-color 0.2s ease-in-out;
  }
  
  .choice:hover {
    background-color: #f0f0f0;
  }
  
  .bg-correct {
    background-color: #a8db8f !important;
    border-color: #a8db8f !important;
    color: #fff;
  }
  
  .bg-wrong {
    background-color: #ffaaaa !important;
    border-color: #ffaaaa !important;
    color: #fff;
  }
  
  .disabled {
    opacity: 0.5;
    cursor: not-allowed;
  }
  
  .next-btn {
    padding: 1em;
    background-color: #1d65a6;
    color: #fff;
    border: none;
    border-radius: 0.5em;
    cursor: pointer;
    transition: background-color 0.2s ease-in-out;
  }
  
  .next-btn:hover {
    background-color: #2d84d1;
  }
  
  .view-result-btn {
    padding: 1em;
    background-color: #1d65a6;
    color: #fff;
    border: none;
    border-radius: 0.5em;
    cursor: pointer;
    transition: background-color 0.2s ease-in-out;
  }
  
  .view-result-btn:hover {
    background-color: #2d84d1;
  }
  </style>
  