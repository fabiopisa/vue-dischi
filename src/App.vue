<template>
  <div id="app">
    <div v-if="!loading">
      <HeaderComp
      :genders="arrGenders"
      @searchGender = 'searchingGender'
      />
      <MainComp 
      :discs="arrDiscsGenders"/>
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
      strGender:'',
      arrDiscsGenders:[],
    }
  },
  created(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then(res =>{
      this.arrDiscs = res.data.response;
      this.arrDiscsGenders = this.arrDiscs;
      this.arrGenders = res.data.response.filter( item =>{
        if(!this.arrGenders.includes(item.genre)){
          return this.arrGenders.push(item.genre)
        }
        console.log(this.arrGenders);
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
    
    searchingGender(text){
      this.strGender = text;
      this.arrDiscsGenders = this.arrDiscs.filter( item =>{
        if(this.strGender === item.genre){
          return true
        }else if(this.strGender === ''){
          return this.arrDiscsGenders = this.arrDiscs
        }
      });
      console.log(this.arrDiscsGenders);
      console.log(this.strGender);
    }
   
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
