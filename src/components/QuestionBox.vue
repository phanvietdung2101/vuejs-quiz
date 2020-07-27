<template>
  <div>
    <b-jumbotron>
      <template slot="lead">
        {{ currentQuestion.question }}
      </template>

      <hr class="my-4" />

      <p v-for="(answer, index) in answers" :key="index">
        {{ answer }}
      </p>

      <b-button variant="primary" >Do Something</b-button>
      <b-button variant="success" v-on:click="next">Next question</b-button>
    </b-jumbotron>
  </div>
</template>

<script>
export default {
  props: {
    currentQuestion: Object,
    next: Function
  },
  computed: {
    answers () {
      let answer = [...this.currentQuestion.incorrect_answers]
      answer.push(this.currentQuestion.correct_answer)
      return answer
    }
  }
}
</script>
