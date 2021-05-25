<template>
  <div id="app">
    <div v-if="!loading">
      <HeaderComp
      :genders="arrGenders"
      @searhGender = "searchingGender"
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
      strGender:'',
    }
  },
  created(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
    .then(res =>{
      console.log(res.data.response);

      this.arrDiscs = res.data.response.filter( item =>{
        if(item.genre === this.strGender){
          return this.arrDiscs.push(item)
        }else if(this.strGender === ''){
          return res.data.response
        }
      });

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
      this.strGender = text
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
