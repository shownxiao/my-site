<template>
<div class="login-box">
        <!-- <p style="font-size: 36px;">Welcome to shown's web</p> -->
  <el-form :model="ruleForm" status-icon :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm input-box">
    <el-form-item label="账号" prop="id">
      <el-input v-model="ruleForm.id" autocomplete="off"></el-input>
    </el-form-item>
    <el-form-item label="密码" prop="pass">
      <el-input type="password" v-model="ruleForm.pass" autocomplete="off"></el-input>
    </el-form-item>
    <el-form-item class="button-box">
      <el-button type="primary" @click="submitForm('ruleForm')">确定</el-button>
      <el-button @click="resetForm('ruleForm')">重置</el-button>
    </el-form-item>
  </el-form>  
  </div>      
</template>
<script>
  export default {
    data() {
      var checkId = (rule, value, callback) => {
        if (!value) {
          return callback(new Error('账号不能为空'));
        }
        else {
                callback();
        }
      };
      var validatePass = (rule, value, callback) => {
        if (value === '') {
          callback(new Error('请输入密码'));
        } else {
          callback();
        }
      };
      return {
        ruleForm: {
          pass: '',
          id: ''
        },
        rules: {
          pass: [
            { validator: validatePass, trigger: 'blur' }
          ],
          id: [
            { validator: checkId, trigger: 'blur' }
          ]
        }
      };
    },
    methods: {
      submitForm(formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            alert('submit!');
          } else {
            console.log('error submit!!');
            return false;
          }
        });
      },
      resetForm(formName) {
        this.$refs[formName].resetFields();
      }
    }
  }
</script>
<style scoped>
.login-box {
        width: 100%;
        text-align: center;
}
.input-box {
        width: 30%;
        margin-left: 32%;
}
.button-box {
        text-align: center;
}
</style>