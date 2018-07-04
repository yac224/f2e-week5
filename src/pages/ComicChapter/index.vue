<script>
import ArrowButton from '@/components/ArrowButton'
import ImageArea from '@/components/ImageArea'
import ChapterThumb from '@/components/ChapterThumb'
function getChapterRoute(id, cid) {
  return {
    name: 'ComicChapter',
    params: {
      id,
      cid
    }
  }
}
export default {
  name: 'comicChapter',
  data() {
    return {
      pages: [],
      page: null,
      chapter: null,
      pchapter: null,
      nchapter: null
    }
  },
  methods: {
    prevHandler() {
      if (this.page > 0) {
        this.page--
      } else if (this.pchapter && confirm('觀看上一話？')) {
        this.prevChapter()
      }
    },
    nextHandler() {
      if (this.page < this.pages.length - 1) {
        this.page++
      } else if (this.nchapter && confirm('觀看下一話？')) {
        this.nextChapter()
      }
    },
    prevChapter() {
      if (this.pchapter) {
        this.$router.replace(this.pchapter)
      }
    },
    nextChapter() {
      if (this.nchapter) {
        this.$router.replace(this.nchapter)
      }
    }
  },
  mounted() {
    let chapter = this.$route.params.cid
    if (
      chapter % 100 < 1 ||
      chapter % 100 > 10 ||
      chapter / 100 > 3 ||
      chapter / 100 < 1
    ) {
      this.$router.replace({
        name: 'ComicsDetail',
        params: { id: this.$route.params.id }
      })
    } else {
      this.pages = [
        '/static/images/p1.jpg',
        '/static/images/p2.jpg',
        '/static/images/p3.jpg',
        '/static/images/p4.jpg',
        '/static/images/p5.jpg',
        '/static/images/p6.jpg',
        '/static/images/p7.jpg',
        '/static/images/p8.jpg',
        '/static/images/p9.jpg'
      ]
      this.page = 0
      this.chapter = this.$route.params.cid >> 0
      if (this.chapter % 100 > 1) {
        this.pchapter = getChapterRoute(this.$route.params.id, this.chapter - 1)
      }
      if (this.chapter % 100 < 10) {
        this.nchapter = getChapterRoute(this.$route.params.id, this.chapter + 1)
      }
    }
  },
  components: {
    ArrowButton,
    ImageArea,
    ChapterThumb
  }
}
</script>

<template src="./template.html"></template>
<style lang="scss" src="./style.scss" scoped></style>
