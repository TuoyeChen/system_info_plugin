<script setup lang="ts">

import {Cpu} from "@icon-park/vue-next";
import {onMounted, onUnmounted, ref} from "vue";
defineProps({
  data: {
    type: Object as ()=>CpuData|undefined,
    default: undefined
  },
  title: {
    type: String,
    default: ''
  }
});
const cpu_fullLoad = ref<number>(0)
const getCpuFullLoad = async () =>{
  cpu_fullLoad.value = await window.services.getCpuFullLoad()
}
let cpuTimerId:NodeJS.Timeout;
onMounted(()=>{
  cpuTimerId = setInterval(()=>{
    getCpuFullLoad()
  },1000)
})
onUnmounted(()=>{
  clearInterval(cpuTimerId)
})

</script>

<template>
  <OptionCard title="CPU">
    <template v-slot:icon>
      <cpu theme="outline" size="24" fill="#333"/>
    </template>
    <template v-slot:content>
      <el-descriptions  :column="3">
        <el-descriptions-item :span="3" label="CPU">{{data?.manufacturer}} {{data?.brand}}</el-descriptions-item>
        <el-descriptions-item label="核心">{{data?.physicalCores}}</el-descriptions-item>
        <el-descriptions-item label="线程">{{data?.performanceCores}}</el-descriptions-item>
        <el-descriptions-item label="使用率"><span style="color:#ff4600;">{{cpu_fullLoad}}%</span></el-descriptions-item>
      </el-descriptions>
    </template>
  </OptionCard>
</template>

<style scoped>

</style>