<template>
  <div id="app">
    <PageHeader/>
    <transition name="fade" mode="out-in" appear>
      <router-view :style="{padding:'60px 0 40px 0'}" :key="$route.fullPath" />
    </transition>
    <PageFooter/>
  </div>
</template>

<script>
import PageHeader from '@/components/PageHeader'
import PageFooter from '@/components/PageFooter'
export default {
  name: 'App',
  components: {
    PageHeader,
    PageFooter
  }
}
</script>

<style lang="scss" src="./assets/style/main.scss"></style>
