<template>
  <div class="styleEditor" ref="container">
    <div class="code" v-html="codeInStyleTag"></div>
    <pre class="" v-html="highlightedCode"></pre>
  </div>
</template>

<script>
  import Prism from 'prismjs'

  export default {
    name: 'Editor',
    props: ['code'],
    computed: {
      /**
       * 将传入的code嵌入style，使得样式能够生效
       * @return {string}
       */
      codeInStyleTag: function () {
        return `<style>${this.code}</style>`
      },
      /**
       * 使用Prism高亮代码
       * @return {*}
       */
      highlightedCode: function () {
        return Prism.highlight(this.code, Prism.languages.css)
      },
    },
    methods: {
      goBottom() {
        this.$refs.container.scrollTop = 100000
      },
    },
  }

</script>

<style scoped>
  pre {
  }

  @media (max-width: 500px) {
    pre {
    }
  }

  .code {
    display: none;
  }
</style>
