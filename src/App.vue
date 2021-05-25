<template>
  <div id="app">
    <div v-if="!loading">
      <HeaderComp
      :genders="arrDiscs"
      />
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
      arrGenders:[],
    }
  },
  created(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then(res =>{
      console.log(res.data.response);
      this.arrDiscs = res.data.response;
      this.arrGenders = res.data.response.filter( item =>{
        if(!this.arrGenders[item.genre].includes(res.data.response[item.genre])){
          return this.arrGenders.push(res.data.response[item]);
        };
      });
      this.loading = false;
    })
    .catch(err =>{
      console.log(err);
    })
  },
  computed:{
    
  },
  methods:{
    
    /* this.arrGenders = this.arrDiscs.filter( item =>{
      if(!this.arrGenders[item.genre].includes(item.genre)){
        this.arrGenders.push(item);
      };
      console.log(this.arrGenders);
      return this.arrGenders
    }), */
   
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
