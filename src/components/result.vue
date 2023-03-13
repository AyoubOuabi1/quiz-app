<script >
export default {
    props:[
        'score',
    ]
}
</script>

<template>
    <div class="container">
        <div class=" text-center mt-4">
            <h3 style="color:rgb(8, 152, 119);">
                Quiz Instractions
            </h3> 
        </div>


       <ul class="fs-5 mt-5 p-2" style="width:70%;margin: auto;">
            Your Score is ({{ score }}/11)
       </ul>
       <div class=" text-center mt-4">
        <button @click="$emit('start-quiz')" type="button" class="btn btn-success ms-3">Start</button>

        </div>
    </div>

</template>
<style>

</style>