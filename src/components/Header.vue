<template>
  <div>
    <b-nav tabs>
      <b-nav-item disable>Quiz</b-nav-item>
      <b-nav-item disable>Counter {{ numCorrect }}/ {{ numTotal }}</b-nav-item>
    </b-nav>
  </div>
</template>
<script>
export default {
  props: [
    'numCorrect',
    'numTotal'
  ]
}
</script>
