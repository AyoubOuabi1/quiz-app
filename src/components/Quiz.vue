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
    <div class="question">{{ questions[currentQuestion].question }}</div>
    <div class="choices">
        <div v-for="(choice,index) in questions[currentQuestion].choices" :value="index" :key="index" class="choice" :class="getChoiceClass(index)" @click="getAnswer(index)">{{ choice }}</div>
    </div>
    <button v-if="!completed"  type="button" class="btn btn-success ms-3" @click="newQuestion">Next</button>
    <button v-else type="button" class="btn btn-success ms-3" @click="$emit('return_result',score)">View result</button>
</template>
<style scoped>
.question {
    font-weight: bold;
    margin: 2em auto;
}
.choices{
    display: flex;
}
.choice{
    margin: 1em auto;
    border: 2px solid #000;

    padding: 1em;
}

</style>