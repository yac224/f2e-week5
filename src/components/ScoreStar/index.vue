<script>
export default {
  name: 'scoreStar',
  props: {
    score: {
      type: Number,
      default: 0
    }
  },
  computed: {
    scoreClass() {
      let num = this.score > 5 ? 5 : this.score < 0 ? 0 : this.score
      return 'star-' + num
    }
  }
}
</script>

<template src="./template.html"></template>
<style lang="scss" src="./style.scss" scoped></style>
