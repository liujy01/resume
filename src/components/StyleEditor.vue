<template>
  <div class="styleEditor" ref="container">
    <div class="code" v-html="codeInStyleTag"></div>
    <pre class="" v-html="highlightedCode"></pre>
  </div>
</template>

<script type="text/ecmascript-6">
  import Prism from 'prismjs'

  export default {
    name: 'styleEditor',
    props: ['code'],
    computed: {
      highlightedCode: function () {
        return Prism.highlight(this.code, Prism.languages.css)
      },
      codeInStyleTag: function () {
        return `<style>${this.code}</style>`
      }
    },
    methods: {
      goBottom() {
        this.$refs.container.scrollTop = 100000
      }
    }
  }
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">
  .code
    display: none
</style>
