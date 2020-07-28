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
            @click.prevent="selectAnswer(index)"
          >
            {{ answer }}
          </b-list-group-item>
        </b-list-group>
      </div>
      <b-button variant="primary" v-on:click="previous">Privious question</b-button>
      <b-button variant="success" v-on:click="next">Next question</b-button>
    </b-jumbotron>
  </div>
</template>

<script>
export default {
  props: {
    currentQuestion: Object,
    next: Function,
    previous: Function
  },
  data () {
    return {
      seletedIndex: null
    }
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
      this.seletedIndex = index
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
.list-group-item:hover {
  background: #EEE;
}
</style>
