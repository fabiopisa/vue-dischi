<template>
  <div id="app">
    <HeaderComp/>
    <MainComp 
    :discs="arrDiscs"/>
  </div>
</template>

<script>
import axios from 'axios';
import HeaderComp from './components/HeaderComp.vue';
import MainComp from './components/MainComp.vue';

export default {
  name: 'App',
  data(){
    return{
      axios,
      arrDiscs:[],
    }
  },
  created(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then(res =>{
      console.log(res.data.response);
      this.arrDiscs = res.data.response
    })
    .catch(err =>{
      console.log(err);
    })
  },
  components: {
    HeaderComp,
    MainComp
    
  },
  
}
</script>

<style lang="scss">
@import '~bootstrap/scss/bootstrap';
@import '@/assets/styles/general.scss';
</style>
