<template>
  <div style="margin:100px;height:400px;width:300px;background:pink;overflow:hidden;" ref="lyrics">
   <ul>
        <li>1234</li>
        <li>etretr</li>
        <li>1434324</li>
        <li>qwrew</li>
        <li>1234</li>
        <li>etretr</li>
        <li>1434324</li>
        <li>qwrew</li>
        <li>1234</li>
        <li>etretr</li>
        <li>1434324</li>
        <li>qwrew</li>
        <li>1234</li>
        <li>etretr</li>
        <li>1434324</li>
        <li>qwrew</li>
    </ul>
    
  </div>
</template>

<script>
import BScroll from 'better-scroll';
export default {
name:"Home",
 mounted() {
      this.$nextTick(() => {
        this._initScroll();
      })
    },
    methods: {
          _initScroll(){
      new BScroll(this.$refs.lyrics,{
        mouseWheel:true
      })
    }
    },
}
</script>

<style>
li{
    height: 50px;
}
</style>