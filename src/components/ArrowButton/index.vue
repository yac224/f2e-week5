<script>
export default {
  name: 'arrowButton',
  props: {
    direction: {
      type: Number,
      default: 3
    }
  },
  computed: {
    directionClass() {
      switch (this.direction) {
        case 0:
          return 'up'
        case 1:
          return 'right'
        case 2:
          return 'down'
        default:
          return 'left'
      }
    }
  }
}
</script>

<template src="./template.html"></template>
<style lang="scss" src="./style.scss" scoped></style>
