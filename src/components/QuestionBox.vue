<template>
    <div >
        <b-card class="mb-3" :title="questionInfo.number + '. ' + questionInfo.question">
            <b-card-text>
            
            </b-card-text>

            <b-card-text>A second paragraph of text in the card.</b-card-text>

            <a href="#" class="card-link">Card link</a>
            <b-link href="#" class="card-link">Another link</b-link>
        </b-card>
        
    </div>
    
</template>

<script>
export default {
  name: 'QuestionBox',
  props: {
      dataset: Object,
      questionInfo: Object
  }

}
</script>