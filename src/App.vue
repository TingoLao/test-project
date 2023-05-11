<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Hello from './components/Hello.vue'
import checkSteps from "./views/checkSteps.vue";
import emailAnima from "./components/icons/emailAnima.vue";
</script>

<template>
  <header>

    <div class="wrapper">
      <div>
        <emailAnima></emailAnima>
      </div>
      <Hello msg="Let send an email!" />
      <!-- 弹出信封动画组件 -->
      
    </div>


  </header>



  <!-- 邮件内容确认组件 -->
  <checkSteps></checkSteps>

  <!-- 页脚 -->
  <el-footer></el-footer>
</template>


<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: block;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
