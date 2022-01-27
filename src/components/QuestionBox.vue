<template>
    <div>
        <b-card :class="correct ? 'correctCard' : 'incorrectCard'" class="mb-3" :title="questionInfo.number + '. ' + questionInfo.question">
            

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
                    :class="{correct: index == questionInfo.correct_answer}"
                    @change="answeredQuestion(index)"
                    
                    :name="questionInfo.question" 
                    :value="index">
                        {{answer}}
                </b-form-radio>

                <div class="mt-3">Selected: <strong>{{ selected }}</strong></div>
                <div class="mt-3">Answered: <strong>{{ answered }}</strong></div>
                <div class="mt-3">Correct: <strong>{{ correct }}</strong></div>
                <div v-show="answered">
                    <b-badge v-if="selected == this.questionInfo.correct_answer" style="background-color: green; color: white" variant="success">Correct</b-badge>
                    <b-badge v-else style="background-color: red; color: white" variant="danger">Wrong</b-badge>
                </div>
            </b-card-text>

            
        </b-card>
        
    </div>
    
</template>

<script>

import {eventBus} from "../main";

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
          test: '',
          correct: ''
      }
  },
  methods: {
      answeredQuestion(index) {
          this.answered = true
          if (index == this.questionInfo.correct_answer) {
              this.correct = true
              this.messageQuizScore()
          } else {
              this.correct = false
              this.messageQuizScore()
          }
      },
      messageQuizScore() {
        
        eventBus.$emit('questionAnswered', this.correct)
    }
  }

}
</script>

<style lang="scss" scoped>
    .correct {
        background: green
    }
    .correctCard {
        border-color: green !important;
    }
    .incorrectCard {
        border-color: red;
    }
</style>