<template>
  <div class="home">
    
    <HelloWorld msg="Vue Quiz App Challenge"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import dataset from '../assets/questions.json'

export default {
  name: 'Home',
  components: {
    HelloWorld
  },
  data(){
    return {
      dataset: dataset
    }
  }
}
</script>
