<template>
  <div class="wrap d-flex justify-content-center align-items-center flex-column">
    <h3>{{str}}</h3>
    <div class="lds-facebook"><div></div><div></div><div></div></div>
    <h4>Loading...</h4>
  </div>
</template>

<script>
export default {
 name:'LoadingComp',
 props:{
   str:String
 }
}
</script>

<style lang="scss" scoped>
.wrap{
  height: 100vh;
  background-color: #1E2D3B;
  color: #FFFFFF;
  font-weight: bold;
}

.lds-facebook {
  display: inline-block;
  position: relative;
  width: 80px;
  height: 80px;
}
.lds-facebook div {
  display: inline-block;
  position: absolute;
  left: 8px;
  width: 16px;
  background: #dfc;
  animation: lds-facebook 1.2s cubic-bezier(0, 0.5, 0.5, 1) infinite;
}
.lds-facebook div:nth-child(1) {
  left: 8px;
  animation-delay: -0.24s;
}
.lds-facebook div:nth-child(2) {
  left: 32px;
  animation-delay: -0.12s;
}
.lds-facebook div:nth-child(3) {
  left: 56px;
  animation-delay: 0;
}
@keyframes lds-facebook {
  0% {
    top: 8px;
    height: 64px;
  }
  50%, 100% {
    top: 24px;
    height: 32px;
  }
}
</style>