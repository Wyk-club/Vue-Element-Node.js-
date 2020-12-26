<template>
  <!-- 表单校验的基本用法 -->
  <div id="app">
    <el-form inline :model="data" :rules="rules" ref="form" :validate-on-rule-change="false">
      <el-form-item label="审批人" prop="user">
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
        <el-button type="primary" @click="addRule">添加校验规则</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>

export default {
  name: 'app',
  data() {
    return {
      data: {
        user:'',
        region: ''
      },
      rules: {
          user: [
              { required: true, trigger: 'change', message: '用户名必须录入' }
          ]
      }
    }
  },
  methods: {
    onSubmit() {
      this.$refs.form.validate((isValid, errors) => {
        //errors会告知哪个属性校验没通过
        console.log(isValid, errors)
      })
    },
    addRule() {
      const userValidator = (rule, value, callback) => {
        if (value.length >3) {
          callback()
        } else {
          callback(new Error('用户名长度必须大于3'))
        }
      }
      const newRule = [
        ...this.rules.user,
        { validator: userValidator, tirgger: 'change' }
      ]
      this.rules = Object.assign({}, this.rules, { user: newRule })
      //注意：一定要通过Object.assign方法生成一个新的对象，而不是给this.rules.user赋值修改规则（因为el-from的watch只能监听到rules，而监听不到rules下的user的变化）
      //当添加完校验规则之后，这个规则会默认立即生效。可以通过一个属性来控制：validate-on-rule-change
    }
  },
}
</script>

<style>

</style>
