<template>
    <div >
        <b-card class="mb-3" :title="questionInfo.number + '. ' + questionInfo.question">
            

            <b-card-text>
                <!-- <ul>
                    <li v-for="(answer, index) in questionInfo.answers" :key="answer[index]">
                        {{answer}}
                    </li>
                </ul> -->
                <b-form-radio v-for="(answer, index) in questionInfo.answers" :key="answer[index]" v-model="selected" :aria-describedby="ariaDescribedby" name="some-radios" :value="answer">{{answer}}</b-form-radio>

                <div class="mt-3">Selected: <strong>{{ selected }}</strong></div>
            </b-card-text>

            
        </b-card>
        
    </div>
    
</template>

<script>
export default {
  name: 'QuestionBox',
  props: {
      dataset: Object,
      questionInfo: Object
  },
  data(){
      return {
          selected: ''
      }
  }

}
</script>