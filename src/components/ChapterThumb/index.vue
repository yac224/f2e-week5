<script>
export default {
  name: 'chapterThumb',
  props: {
    page: {
      type: Number,
      default: 0
    },
    pages: {
      type: Array,
      required: true
    },
    pchapter: {
      type: Object,
      default: null
    },
    nchapter: {
      type: Object,
      default: null
    }
  },
  methods: {
    clickHandler(page) {
      this.$emit('update:page', page)
    }
  },
  watch: {
    page() {
      if (!this.$el) return false
      let el = this.$el.querySelector('ul')
      // let index = this.pchapter ? this.page + 1 : this.page
      // let target = el.querySelectorAll('li')[index]
      this.$nextTick(() => {
        let target = el.querySelector('li.active')
        if (!target) return false
        el.scrollLeft =
          target.offsetLeft -
          el.offsetLeft -
          el.offsetWidth / 2 +
          target.offsetWidth / 2
      })
    }
  }
}
</script>

<template src="./template.html"></template>
<style lang="scss" src="./style.scss" scoped></style>
