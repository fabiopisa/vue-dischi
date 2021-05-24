<template>
  <div id="app">
    <HeaderComp/>
  </div>
</template>

<script>
import axios from 'axios';
import HeaderComp from './components/HeaderComp.vue';

export default {
  name: 'App',
  data(){
    return{
      axios,
    }
  },
  created(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then (res =>{
      console.log(res.data);
    })
    .cath(err =>{
      console.log(err);
    })
  },
  components: {
    HeaderComp
    
  },
  
}
</script>

<style lang="scss" scoped>
@import '~bootstrap/scss/bootstrap'
</style>
