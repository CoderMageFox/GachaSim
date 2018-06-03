<template>
  <div>
    <div class="resultarea" id="chatContainer">
      <div v-for="item in newsArr">
        {{item}}
      </div>
    </div>
    <div class="says">
      <ul>
        <li @click="getGacha10">氪金十一连抽-常规</li>
        <li @click="getGachaUp10">氪金十一连抽-桃源村UP</li>
        <li @click="getGachaUpOnce">单抽桃源村出奇迹</li>
      </ul>
    </div>

  </div>
</template>

<script>
  export default {
    data () {
      return {
        newsArr:[],
        level5: ['神之御子微微', '幽冥的梅菲尔'],
        level4: ['公主史莱姆', '狂犬多米诺', '七尾.稻荷御澄', '真护·天茧', '莉安夕', '卡库拉拉兹巴', '阿芙莉芒', '宝石迷迷可', '死亡缠绕·萝丝娜', '沼江夜鸣·鵺', '罪骨公主·斯卡莉安'],
        level3: ['MIO', '露库希安', '义贼多米诺', '海歌姬·赛伦', '雷素·鸣', '基雅·库罗', '秋风希露芙', '拉克斯·蕾妮娅', '血口荆棘·辛普拉', '妖蛾子', '高原火角·阿卡铃', '花藕子', '月兔蕾雅', '白浪激流·克洛琪', '桑图艾尔'],
      }
    },
    methods: {
      initChanceArr (chanceArray) {
        let result = [0]
        for (i = 0; i < chanceArray.length; i++) {
          result.push(chanceArray[i] + result[i])
        }
        return result
      },
      cashEggLevel () {
        let level = 0
        let result = Math.random() * 100
        const chance = [1.61, 5.2, 12.5, 80.39, 0.3]
        //设置孵化概率
        const chanceArray = [1.61,6.81,19.31,99.7,100]
        //当前星级分别为1.61%,6.81%,19.31%,99.7%,100%概率出大于等于5/4/3/2/1星
        level = chanceArray.findIndex((element) => {
          return result < element
        })
        return 5-level
      },
      getRandomResult(array){
        let num=parseInt(array.length*Math.random())
        return array[num]
      },
      getGachaResult(level){
        switch (level){
          case 1:return '★杂鱼(天选之非)'
          case 2:return '★★杂鱼'
          case 3:return '★★★'+this.getRandomResult(this.level3)
          case 4:return '★★★★'+this.getRandomResult(this.level4)
          case 5:return '★★★★★'+this.getRandomResult(this.level5)
        }
      },
      getGachaUpResult(level){
        let UpRandom=parseInt(10*Math.random())
        switch (level){
          case 1:return '★杂鱼(天选之非)'
          case 2:return '★★杂鱼'
          case 3:return UpRandom>4?'★★★'+this.getRandomResult(this.level3):'★★★野林之歌·木野子'
          case 4:return UpRandom>4?'★★★★'+this.getRandomResult(this.level4):'★★★★命运之女·拉米娅'
          case 5:return UpRandom>4?'★★★★★'+this.getRandomResult(this.level5):'★★★★★幻翼天角·菲娜'
        }
      },
      addLine(){
        this.newsArr.push('------十一连分割线-------')
      },
      getGachaUpOnce(){
        this.newsArr.push(this.getGachaUpResult(this.cashEggLevel()));
      },
      getGacha10(){
        for (let i=0;i<11;i++){
          this.newsArr.push(this.getGachaResult(this.cashEggLevel()));
        }
        this.addLine()
      },
      getGachaUp10(){
        for (let i=0;i<11;i++){
          this.getGachaUpOnce();
        }
        this.addLine()
      },
    },
    watch: {
      newsArr() {
        this.$nextTick(() => {
          var container = this.$el.querySelector("#chatContainer");
          container.scrollTop = container.scrollHeight;
        })
      }
    }
  }
</script>

<style scoped>
  .says > ul > li {
    margin-bottom: 0.4rem;
    text-align: center;
    font-size: 0.5rem;
    padding: 0.2rem;
    border: 4px dashed gray;
    border-radius: 0.75rem;
  }
  .resultarea{
    text-wrap: normal;
    overflow: scroll;
    border: 5px dashed #3E3410;
    font-size: 0.4rem;
    opacity: 0.6;
    margin-top: 1rem;
    margin-left: 1rem;
    width: 8rem;
    height: 10rem;
    background: #D8D5B0;
  }

</style>
