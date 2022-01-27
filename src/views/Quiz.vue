<template>
  <div class="home">
    
    <HelloWorld msg="Vue Quiz App Challenge"/>
    <quiz-score/>
    <question-box 
       
      v-for="(question, index) in dataset.questions" 
      :key="question[index]" 
      :dataset="dataset"
      :questionInfo="question"
    />
    
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import dataset from '../assets/questions.json'
import QuestionBox from '../components/QuestionBox.vue'
import QuizScore from '../components/QuizScore.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld,
    QuestionBox,
    QuizScore
  },
  data(){
    return {
      dataset: dataset
    }
  }
}
</script>
