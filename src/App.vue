<template>
  <div id="app">
    <div v-if="!loading">
      <HeaderComp/>
      <MainComp 
      :discs="arrDiscs"/>
    </div>
    <div v-else>
      <LoadingComp str="Spotify" />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import HeaderComp from './components/HeaderComp.vue';
import MainComp from './components/MainComp.vue';
import LoadingComp from './components/LoadingComp.vue';

export default {
  name: 'App',
  data(){
    return{
      axios,
      arrDiscs:[],
      loading:true,
    }
  },
  created(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then(res =>{
      console.log(res.data.response);
      this.arrDiscs = res.data.response;
      this.loading = false;
    })
    .catch(err =>{
      console.log(err);
    })
  },
  components: {
    HeaderComp,
    MainComp,
    LoadingComp
    
  },
  
}
</script>

<style lang="scss">
@import '@/assets/styles/general.scss';
</style>
