<template>
  <div id="app">
    <h3>表单的基本用法</h3>
    <el-form inline :model="data">
      <el-form-item label="审批人">
        <el-input v-model="data.user" placeholder="审批人"></el-input>
      </el-form-item>
      <el-form-item labe="活动区域">
        <el-select v-model="data.region" placeholder="活动区域">
          <el-option label="区域一" value="shanghai"></el-option>
          <el-option label="区域二" value="beijing"></el-option>
        </el-select>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="onSubmit">查询</el-button>
      </el-form-item>
    </el-form>
    <el-divider></el-divider>
    <h3>表单校验的基本用法</h3>
    <form-valid-base></form-valid-base>
    <el-divider></el-divider>
    <h3>表单校验的高级用法1 - 动态改变校验规则</h3>
    <form-valid-senior1></form-valid-senior1>
    <el-divider></el-divider>
    <h3>表单校验的高级用法2 - 手动控制校验状态</h3>
    <form-valid-senior2></form-valid-senior2>
  </div>
</template>

<script>
import formValidBase from './form-valid-base.vue'
import formValidSenior1 from './form-valid-senior1.vue'
import formValidSenior2 from './form-valid-senior2.vue'
export default {
  name: 'app',
  components: {
    formValidBase,
    formValidSenior1,
    formValidSenior2
  },
  data() {
    return {
      data: {
        user:'sam',
        region: 'shanghai'
      }
    }
  },
  methods: {
    onSubmit() {
      console.log(this.data)
    }
  },
}
</script>

<style>

</style>
