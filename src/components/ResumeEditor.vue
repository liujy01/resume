<template>
  <div class="resumeEditor" :class="{htmlMode:enableHtml}" ref="container">
    <div v-if="enableHtml" v-html="result"></div>
    <pre v-else>{{result}}</pre>
  </div>
</template>

<script type="text/ecmascript-6">
  import marked from 'marked'

  export default {
    name: 'resumeEditor',
    props: ['markdown', 'enableHtml'],
    computed: {
      result: function () {
        return this.enableHtml ? marked(this.markdown) : this.markdown
      }
    },
    methods: {
      goBottom: function () {
        this.$refs.container.scrollTop = 100000
      },
      goTop: function () {
        this.$refs.container.scrollTop = 0
      }
    }
  }
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">
  .htmlMode
    animation: flip 2s

  @keyframes flip
    from
      opacity: 0
    to
      opacity: 1
</style>
