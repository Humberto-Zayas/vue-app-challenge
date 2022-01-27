<template>
    <div >
        <b-card class="mb-3" :title="questionInfo.number + '. ' + questionInfo.question">
            

            <b-card-text>
                <!-- <ul>
                    <li v-for="(answer, index) in questionInfo.answers" :key="answer[index]">
                        {{answer}}
                    </li>
                </ul> -->
                <b-form-radio 
                    v-model="selected" 
                    v-for="(answer, index) in questionInfo.answers" 
                    :key="answer[index]" 
                    :class="{correct: answer[index] == questionInfo.correct_answer}"
                    @change="answeredQuestion(answer[index])"
                    :name="questionInfo.question" 
                    :value="answer">
                        {{answer}}
                </b-form-radio>

                <div class="mt-3">Selected: <strong>{{ selected }}</strong></div>
                <div class="mt-3">Answered: <strong>{{ answered }}</strong></div>
                <div>
                    <b-badge style="background-color: green; color: white" variant="success">Correct</b-badge>
                    <b-badge style="background-color: red; color: white" variant="danger">Wrong</b-badge>
                </div>
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
          selected: '',
          answered: false,
          test: ''
      }
  },
  methods: {
      questionAnswered() {
          this.$emit('answered')
          return this.answered = true
      }
  }

}
</script>

<style lang="scss" scoped>
    .correct {
        background: green
    }
</style>