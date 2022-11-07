<template>
  <div>
    <Header></Header>
    <!-- 路口组件出口的地方 -->
    <router-view></router-view>
    <Footer></Footer>
  </div>
</template>

<script>
// 引入组件
import Header from './components/Header'
import Footer from './components/Footer'
export default {
  name: 'App',
  // 注册组件
  components:{
    Header,Footer
  }
}
</script>

<style scoped>
  
</style>