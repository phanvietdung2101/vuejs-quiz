<template>
  <div>
    <b-jumbotron>
      <template slot="lead">
        {{ currentQuestion.question }}
      </template>

      <hr class="my-4" />
      <div>
        <b-list-group>
          <b-list-group-item
            v-for="(answer, index) in answers"
            :key="index"
          >
            {{ answer }}
          </b-list-group-item>
        </b-list-group>
      </div>
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
  },
  methods: {
    selectAnswer (index) {
      console.log(index)
    }
  },
  mounted () {
    console.log(this.currentQuestion)
  }
}
</script>
<style scoped>
.list-group {
  margin-bottom: 15px;
}
.btn {
  margin: 0 5px;
}
</style>
