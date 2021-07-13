<template>
  <div id="app">
    <Header @search="searchMovie"/>
    <Main :movieTitle="titolo"/>
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
    searchMovie(text){
      this.titolo = text;
    }
  }
}
</script>

<style lang="scss">
@import 'bootstrap';
@import './style/commons.scss';

</style>
