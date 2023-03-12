<script>
export default {
    props:[
        'data',
        'currentQuestion'
    ],
    data(){
        return {
            isCorrect :false,
        }
    }
}
</script>
<template>
    <div class="question">{{ data[currentQuestion].question }}</div>
    <div class="choices">
        <div v-for="(choice,index) in data[currentQuestion].choices" :key="index" class="choice">{{ choice }}</div>
    </div>
    <!-- <div v-for="(question,index) in data" :key="index">{{ question.question }}</div> -->
    <div>{{ currentQuestion }}</div>
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