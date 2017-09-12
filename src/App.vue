<template>
  <div id="app">
    <StyleEditor></StyleEditor>
  </div>
</template>

<script>
  import StyleEditor from './components/StyleEditor'
  import ResumeEditor from './components/ResumeEditor'
  export default {
    name: 'app',
    components: {
      StyleEditor,
      ResumeEditor
    },
    data() {
      return {
      }
    },
    created() {

    },
    methods: {},

  }
</script>

<style scoped>

</style>
