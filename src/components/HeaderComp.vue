<template>
  <header>
    <div class="box-logo col-1 offset-1">
        <div class="logo"></div>
    </div>
    <div class="offset-8 col-1">
      <select name="album" id="generis" placeholder="Generi">
        <option
        @click="resetStr()" 
        value="all">
          All
        </option>
        <option
        v-for="(gender, index) in genders" :key="index"
        @click="writheStr(gender.genre)"
        value="gender.genre">
        {{gender.genre}}
        </option>
      </select>
    </div>
  </header>
</template>

<script>
export default {
 name:'HeaderComp',
 data(){
   return{
     strSearchGender:'',
   }
 },
 props:{
   genders:Array
 },
 methods:{
   writheStr(object){
     this.$emit("searchGender",this.strSearchGender = object);
     console.log(this.strSearchGender);
   },
   resetStr(){
     this.strSearchGender ="";
     this.writheStr('');
   }
 }
}
</script>

<style lang="scss" scoped>

header{
  height: 70px;
  background-color:#2E3A46 ;
  display: flex;
  align-items: center;
  .box-logo{
    .logo{
      height: 50px;
      width: 50px;
      border-radius: 50%;
      background-color: #1ED560
    };
  };
  select{
    background-color:#1E2D3B ;
    padding: 5px 30px;
    color: #FFFFFF;
    border: none;
    border-radius: 5px;
    option{
      background-color: #3b4550;
    };
  };
}

</style>