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
  /**
 * Eric Meyer's Reset CSS v2.0 (http://meyerweb.com/eric/tools/css/reset/)
 * http://cssreset.com
 */
  html, body, div, span, applet, object, iframe,
  h1, h2, h3, h4, h5, h6, p, blockquote, pre,
  a, abbr, acronym, address, big, cite, code,
  del, dfn, em, img, ins, kbd, q, s, samp,
  small, strike, strong, sub, sup, tt, var,
  b, u, i, center,
  dl, dt, dd, ol, ul, li,
  fieldset, form, label, legend,
  table, caption, tbody, tfoot, thead, tr, th, td,
  article, aside, canvas, details, embed,
  figure, figcaption, footer, header, hgroup,
  menu, nav, output, ruby, section, summary,
  time, mark, audio, video {
    margin: 0;
    padding: 0;
    border: 0;
    font-size: 100%;
    font: inherit;
    vertical-align: baseline;
  }
  /* HTML5 display-role reset for older browsers */
  article, aside, details, figcaption, figure,
  footer, header, hgroup, menu, nav, section {
    display: block;
  }
  body {
    line-height: 1;
  }
  ol, ul {
    list-style: none;
  }
  blockquote, q {
    quotes: none;
  }
  blockquote:before, blockquote:after,
  q:before, q:after {
    content: '';
    content: none;
  }
  table {
    border-collapse: collapse;
    border-spacing: 0;
  }

</style>
