<template>
  <div id="app">
    <Header/>
    <Main/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import './style/commons.scss'

export default {
  name: 'App',
  components: {
    Header
  }
}
</script>

<style lang="scss">
@import 'bootstrap';

</style>
