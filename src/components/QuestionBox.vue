<template>
  <div>
    <b-jumbotron>
      <template slot="lead">
        {{ currentQuestion.question }}
      </template>

      <hr class="my-4" />

      <p>
        {{ question }}
      </p>

      <b-button variant="primary" >Do Something</b-button>
      <b-button variant="success" v-on:click="nextQuestion()">Next question</b-button>
    </b-jumbotron>
  </div>
</template>

<script>
export default {
  props: {
    currentQuestion: Object
  }
}
</script>
