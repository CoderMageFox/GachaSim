<template>
  <div>
    <div id="app">
      <pre v-html="highlightedCode" class="codeclass">{{code}}</pre>
    </div>
    <pre v-html="styleCode" ></pre>
  </div>
</template>
<script>
  import Prism from 'prismjs'
  export default {
    name: 'app',
    components: {Prism},
    data() {
      return {
        code:'',
        finalCode:

`
       /*一般来说,为了网页效果的平滑过渡,我们需要增加一些简单的过渡动画.*/
       *{transition: all .3s}
       /*写一个网页,首先要清除CSS的默认样式*/
       html,body{margin: 0;
                 padding: 0;
                 height:100%;}
       *{box-sizing: border-box;}
       *::before{box-sizing: border-box;}
       *::after{box-sizing: border-box;}
       *{margin: 0; padding: 0;}
       /*似乎白色的背景十分刺眼,我们需要一个让人更加舒服一些的颜色.*/
       #app pre{background:#252525;
                  color:white;}
       /*这样可不适合我们进行阅读.*/
       .codeclass{overflow: auto;
                  width: 50vw;
                  height: 100vh;}
       /*如果你想要代码看起来不凌乱,那么一定要有代码高亮.*/
       .token.selector{ color: rgb(133,153,0); }
       .token.property{ color: rgb(187,137,0); }
       .token.punctuation{ color: yellow; }
       .token.function{ color: rgb(42,161,152); }
       /*一些简单的CSS Hack,比如虚线双重边框,也是一个前端应该掌握的.*/
       .codeclass{outline:2px dashed white;
                  outline-offset:-10px;}
       /*2017年,哪怕是Web端,也应该实现一些简单的3D效果了.*/
        html{perspective: 1000px;}
      .codeclass{position: fixed; left: 0; top: 0;
                -webkit-transition: none;
                transition: 1s;
                -webkit-transform: rotateY(360deg) translateZ(-200px);
                transform: rotateY(360deg) translateZ(-200px);
                }
        `
      }
    },
    created() {

      var PassedTime = 0
      setInterval(()=>{
        this.code = this.finalCode.substring(0,PassedTime)
        PassedTime+=1
      },10)

    },
    methods: {},
    computed:{
      styleCode(){
        return '<style>'+ this.code +'</style>'
      },
      highlightedCode: function () {
        return Prism.highlight(this.code, Prism.languages.css)
      },
    },
  }
</script>

