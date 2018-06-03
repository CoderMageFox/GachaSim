<template>
  <div id="app">
    <img src="../static/PICS/background.jpg" class="background" @click="showChoose">
    <welcome v-if="!chooseDisplay"></welcome>
    <choose v-if="chooseDisplay" ></choose>
  </div>
</template>

<script>
  import welcome from './components/welcome'
  import choose from './components/choose'
  export default {
    name: 'app',
    components: {
      welcome,
      choose,
    },
    data () {
      return {
        chooseDisplay: 0,
        newsArr:[],
      }
    },
    methods: {
      showChoose:function () {
        this.chooseDisplay=1;
      },
    },
  }
</script>

<style >
  #app{
    overflow: hidden;
  }
  .background{
    width: 100%;
    height: 100%;
    position: absolute;
    overflow: hidden;
    z-index: -1;
  }
  .says{
    font-size: 0.4rem;
    left: 0.1rem;
    position: absolute;
    top: 13rem;
  }
</style>
