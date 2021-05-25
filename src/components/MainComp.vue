<template>
  <main class="d-flex">
    <section class="box-discs col-10 offset-1">
      <div 
      v-for="(disc, index) in discs" :key="index"
      class="box-disco col-12 col-md-6 col-lg-2 p-3 m-0 p-lg-0 m-lg-3 text-center">

        <div class="box-background p-3">
          <img class="img-fluid" :src="disc.poster" :alt="disc.title">
          <h3>{{disc.title}}</h3>
          <div>
            <h4>{{disc.author}}</h4>
            <h4>{{disc.year}}</h4>
          </div>
        </div>

      </div>
    </section>

  </main>
</template>

<script>
export default {
 name:'MainComp',
 props:{
   discs: Array
 }
};

</script>

<style lang="scss" scoped>
main{
  padding: 90px 0;
  .box-discs{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    .box-disco{
      .box-background{
        background-color:#2E3A46 ;
        display: flex;
        flex-direction: column;
        align-items: center;
        height: 100%;
        img{
          width: 100%;
        };
        h3{
          color: #FFFFFF;
          font-size: 20px;
          text-transform: uppercase;
          font-weight: bold;
          margin:20px 0 10px;
        };
        h4{
          font-size: 15px;
          color:#737771; 
          margin-bottom: 0;
          &:last-child{
            font-size: 13px
          };      
        };
      };

    };
  };
};
</style>