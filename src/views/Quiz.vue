<template>
  <div class="home">
    
    <HelloWorld msg="Vue Quiz App Challenge"/>
    <question-box />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import dataset from '../assets/questions.json'
import QuestionBox from '../components/QuestionBox.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld,
    QuestionBox
  },
  data(){
    return {
      dataset: dataset
    }
  }
}
</script>
