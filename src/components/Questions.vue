<template>
  <div class="questions-ctr">

    <div class="progress">
      <div class="bar"
           :style="{width: `${questionsAnsweredProp / questionsProp.length * 100}%` }"></div>
      <div class="status">
        {{ questionsAnsweredProp }} out of
        {{ questionsProp.length }} questions answered
      </div>
    </div>
    <div class="single-question"
         v-for="(question, questionIndex) in questionsProp"
         :key="question.q"
         v-show="questionsAnsweredProp === questionIndex"
    >
      <div class="question">
        {{ question.q }}
      </div>
      <div class="answers">
        <div class="answer"
             v-for="answer in question.answers"
             :key="answer.text"
             @click.prevent="selectAnswer(answer.is_correct)"
        >
          {{ answer.text }}
        </div>
      </div>
    </div>

    <br/>
    <br/>
    <hr/>

    <div>
      <h3>App Data</h3>
      <p><strong>questions.length:</strong> {{ questionsProp.length }}</p>
      <p><strong>questions:</strong> {{ questionsProp }}</p>
    </div>

  </div>
</template>

<script>
export default {
  name: "Questions",
  props: {
    questionsProp: {type: Array, required: true},
    questionsAnsweredProp: {type: Number, required: true}
  },
  emits: ['question-answered'],
  methods: {
    selectAnswer(is_correct) {
      console.log('... selectAnswer() ...', is_correct)
      this.$emit("question-answered", is_correct
      )
    }
  }
}
</script>



