<template>
  <div id="app">
    <el-button @click="show">按钮</el-button>
  </div>
</template>

<script>

export default {
  name: 'App',
  methods: {
    show() {
      this.$message('element-ui提示')
    }
  },
}
</script>

<style>

</style>
