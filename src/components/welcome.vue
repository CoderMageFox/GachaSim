<template>
  <div>
    <div id="app">
      <div class="basement">
      <pre class="says">{{code}}</pre>
      </div>
    </div>
  </div>
</template>
<script>

  export default {
    name: 'app',
    data() {
      return {
        code:'',
        finalCode:
`  最近刚好没钱用,非洲人快点来给我送钱吧～

   说明:1.本模拟器概率完全参照官方公布的抽奖概率表,

       没有做十一连保底逻辑,结果仅供参考

       (但是因为是官方概率,还是可供参考的,非洲人自觉)

       2.写完一共花了我四个小时,仓促可能会有bug,见谅。

        `
      }
    },
    created() {

      var PassedTime = 0
      setInterval(()=>{
        this.code = this.finalCode.substring(0,PassedTime)
        PassedTime+=1
      },30)

    },
    computed:{
      styleCode(){
        return this.code
      },
    },
  }
</script>
<style>


</style>

