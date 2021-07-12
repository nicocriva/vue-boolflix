<template>
  <div id="app">
    <Header @search="searchMovie"/>
    <div>{{titolo}}</div>
    <Main/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'


export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data(){
    return{
      titolo: '',
    }
  },
  methods:{
    searchMovie(element){
      this.titolo = element;
    }
  }
}
</script>

<style lang="scss">
@import 'bootstrap';
@import './style/commons.scss';

</style>
