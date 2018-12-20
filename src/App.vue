<template>
  <div id="app">
    <my-header></my-header>
    <Tab></Tab>
    <router-view/>
  </div>
</template>

<script>
import MyHeader from './components/my-header/header'
import Tab from './components/tab/tab'
export default {
  name: 'App',
  components: {
    MyHeader,
    Tab
  }
}
</script>

<style lang="stylus" scoped>

</style>
