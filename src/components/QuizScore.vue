<template>
    <div>
        <h3>Quiz Results</h3>
        <p>You Got {{tally}}/{{dataset.questions.length}} correct.</p>
        <p><strong>Percentage</strong>: {{(tally/dataset.questions.length) * 100 }}</p>
        <!-- <div class="mt-3 alert alert-secondary">
            {{tally}}
        </div> -->
    </div>
</template>

<script>

 import {eventBus} from "../main";

export default {
name: 'QuizScore',
props: {
    dataset: Object
},
data() {
    return {
        tally: 0
    }
},
created() {
        eventBus.$on('questionAnswered', (correct) => {
            
            if(correct == true) {
                this.tally += 1
            } else {
                this.tally -= Math.max(0, this.tally - 1);
            }
        });
    }
}

</script>

<style lang="scss" scoped>
    .score {
        color: red;
    }
</style>