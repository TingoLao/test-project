<script setup>
import Step1 from "../components/Step1.vue";
import Step2 from "../components/Step2.vue";
import Step3 from "../components/Step3.vue";
import Step4 from "../components/Step4.vue";
</script>

<template>
  <main>
    确认用户邮件步骤的页面
    <el-container id="container">
      <Step1></Step1>
      <div id="diliverLong"></div>
      <Step2></Step2>
      <div id="diliverLong"></div>
      <Step3></Step3>
      <div id="diliverLong"></div>
      <Step4></Step4>
    </el-container>

  </main>
</template>

<script>

</script>

<style>
#container {
  display: flex;
  flex-direction: column;
  text-align: -webkit-center;
  padding-top: 40px;
}

/* 分割线样式 */
#diliverLong {
  height: 1px;
  width: 90%;
  align-self: center;
  background-color: #999999;
  margin-bottom: 15px;
  margin-top: 20px;
}

</style>