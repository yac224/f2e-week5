<script>
import axios from 'axios'
import ScoreStar from '@/components/ScoreStar'
export default {
  name: 'comicDetail',
  data() {
    return {
      detail: null
    }
  },
  mounted() {
    axios
      .get('/api/detail/' + this.$route.params.id)
      .then(res => {
        if (res.data.chapters) {
          this.detail = res.data
        } else {
          this.$router.replace('/comics')
        }
      })
      .catch(() => {
        this.$router.replace('/comics')
      })
  },
  components: {
    ScoreStar
  }
}
</script>

<template src="./template.html"></template>
<style lang="scss" src="./style.scss" scoped></style>
