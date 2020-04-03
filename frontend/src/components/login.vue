<template>
  <section class="login_container">
    <section class="header">
      <p @click="toSignUp" :class="{'active': currentItem==='signup'}">Sign up</p>
      <el-divider direction="vertical"></el-divider>
      <p @click="toLogin" :class="{'active': currentItem==='login'}">Login</p>
    </section>
    <section v-if="currentItem==='signup'" class="login_main">
      <el-form label-position="top" :model="signForm" :rules="formRules" label-width="100px">
        <el-form-item label="username" prop="username">
          <el-input v-model="signForm.username" size="small"></el-input>
        </el-form-item>
        <el-form-item label="password" prop="password">
          <el-input v-model="signForm.password" type="password" size="small"></el-input>
        </el-form-item>
        <el-form-item label="confirm password" prop="cpassword">
          <el-input v-model="signForm.cpassword" type="password" size="small"></el-input>
        </el-form-item>
        <el-form-item>
          <el-checkbox v-model="anonymous" label="submit anonymously"></el-checkbox>
        </el-form-item>
        <el-form-item>
          <el-button type="warning">{{anonymous ? 'Submit anonymously' : 'Sign up'}}</el-button>
        </el-form-item>
      </el-form>
    </section>
    <section v-else class="login_main">
      <el-form label-position="top" :model="userForm" label-width="100px">
        <el-form-item label="username">
          <el-input v-model="userForm.username" size="small"></el-input>
        </el-form-item>
        <el-form-item label="password">
          <el-input v-model="userForm.password" type="password" size="small"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="warning">Login and save</el-button>
        </el-form-item>
      </el-form>
    </section>
  </section>
</template>
<script>

export default {
  name: 'Login',
  data() {
    var validatePass = (rule, value, callback) => {
      if (value === '') {
        callback(new Error('Please input confirm password.'));
      } else if (value !== this.userForm.password) {
        callback(new Error('Password and confirm password do not match!'));
      } else {
        callback();
      }
    };
    return {
      signForm:  {
        username: '',
        password: '',
        cpassword: ''
      },
      userForm: {
        username: '',
        password: ''
      },
      currentItem: 'signup',
      anonymous: false,
      formRules: {
        username: [{
          required: true,
          message: 'Please input username.',
          trigger: 'blur'
        }],
        password: [{
          required: true,
          message: 'Please input password.',
          trigger: 'blur'
        }],
        cpassword: [{ 
          validator: validatePass,
          trigger: 'blur' 
        }]
      },
       formRules2: {
        username: [{
          required: true,
          message: 'Please input username.',
          trigger: 'blur'
        }],
        password: [{
          required: true,
          message: 'Please input password.',
          trigger: 'blur'
        }]
      }
    }
  },
  methods: {
    toSignUp() {
      this.currentItem = 'signup';
    },
    toLogin() {
      this.currentItem = 'login';
    }
  }
}
</script>
<style scoped>
  .header {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 60px;
    line-height: 60px;
    background-color: #323f4f;
    color:#fff;
    font-size: 28px;
    padding-left: 30px;
  }
  .header p {
    display: inline-block;
    margin: 0;
    cursor: pointer;
  }
  .header .active {
    color: #ffd04b;
  }
  .login_container {
    width: 100%;
    height: 100%;
    position: fixed;
    background: url('../assets/img/bg_login.jpg') no-repeat;
    background-size: 100%;
    background-position: center;
    display: flex;
    flex-direction: column;
    align-items: center;
    align-content: center;
    justify-content: center;
  }
  .login_main {
    width: 400px;
    height: 450px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background-color: rgba(255, 255, 255, .2);
  }
  .el-form{
    height: auto;
  }
  .el-form /deep/ .el-form-item {
    margin-bottom: 20px;
  }
  .el-form-item /deep/ .el-input__inner {
    width: 240px;
  }
  .el-form /deep/ .el-form-item__label, .el-form /deep/ .el-checkbox__label {
    font-size: 20px;
    color: #323f4f;
    font-weight: 500;
    padding-bottom: 0;
  }
  .el-form /deep/ .el-button {
    font-size: 20px;
  }
  .el-form /deep/ .el-checkbox__input.is-checked .el-checkbox__inner, .el-form /deep/ .el-checkbox__input.is-indeterminate .el-checkbox__inner {
    background-color: #e6a23c;
    border-color: #e6a23c;
  }
  .el-form /deep/ .el-checkbox__input.is-focus .el-checkbox__inner,.el-form /deep/ .el-checkbox__inner:hover {
    border-color: #e6a23c;
  }

  @media screen and (max-width: 379px) {
    .login_container {
      background-size: auto 100%;
    }
    .login_main {
      width: 100%;
      height: 100%;
    }
  }
</style>

