<script setup lang="ts">
import {onMounted} from "vue";


function closeWindow(): void {
  window.close()
}
// const vsConsole = new VConsole();
// console.log(vsConsole);
onMounted(()=>{
  addEventListener('keyup',(evt)=>{
    switch (evt.key){
      case 'Escape':{
        window.close();
        break;
      }
    }
  })
})
</script>

<template>

  <div class="container">
    <div class="btnSpace">
      <div tabindex="0" @click="closeWindow" class="btn" style="background-color: #fb625f;cursor: pointer"/>
      <div class="btn" style="background-color: #f9c57a"/>
      <div class="btn" style="background-color: #8ac872"/>
    </div>
    <div class="dragSpace">

    </div>

  </div>
</template>

<style scoped lang="less">
.container {
  background-color: #d9d8d9;
  padding: 0 10px;
  height: 30px;
  display: flex;
  justify-content: space-between;

  .btnSpace {
    flex: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 5px;

    .btn {
      height: 12px;
      width: 12px;
      border-radius: 100%;
      background-image: linear-gradient(rgba(255, 255, 255, 0) 0, rgba(255, 255, 255, 0) 50%, #fff 95%, #fff 100%);
      box-shadow: 0 2px 0 rgba(255, 255, 255, .8), inset 0 0 3px 1px rgba(0, 0, 0, .6), 0 -1px 1px 1px rgba(0, 0, 0, .4);
      -webkit-box-shadow: 0 2px 0 rgba(255, 255, 255, .8), inset 0 0 3px 1px rgba(0, 0, 0, .6), 0 -1px 1px 1px rgba(0, 0, 0, .4);
    }
  }
  .dragSpace {
    flex: 1;
    -webkit-app-region: drag;
  }
}
</style>
