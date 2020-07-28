<template>
  <div id="App">
    <Header
      :numCorrect="numCorrect"
      :numTotal="numTotal"
    />

    <b-container class="bv-example-row container">
      <b-row>
        <b-col class="col-6 offset-3" >
          <QuestionBox
          v-if="questions.length"
          :currentQuestion="questions[index]"
          :next="next"
          :increment="increment"
          />
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import Header from './components/Header'
import QuestionBox from './components/QuestionBox'

export default {
  name: 'App',
  components: {
    Header,
    QuestionBox
  },
  data () {
    return {
      totalQuestion: 5,
      questions: [],
      index: 0,
      numCorrect: 0,
      numTotal: 0
    }
  },
  methods: {
    next () {
      if (this.index < this.totalQuestion - 1) {
        this.index++
      } else {
        alert(`${this.numCorrect} correct answer`)
      }
    },
    previous () {
      this.index--
    },
    increment (isCorrect) {
      if (isCorrect) {
        this.numCorrect++
      }
      this.numTotal++
    }
  },
  mounted () {
    fetch(`https://opentdb.com/api.php?amount=${this.totalQuestion}&type=multiple`, {
      method: 'get'
    })
      .then((response) => {
        return response.json()
      })
      .then((jsonData) => {
        this.questions = jsonData.results
        console.log(this.questions)
      })
  }
}
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
