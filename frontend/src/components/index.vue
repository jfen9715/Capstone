<template>
  <div class="container">
    <section class="header">
      <el-menu
        :default-active="currentItem"
        class="el-menu-demo"
        mode="horizontal"
        menu-trigger="hover"
        @select="itemChange"
        background-color="#323f4f"
        text-color="#fff"
        active-text-color="#e89c2c">
        <el-menu-item index="1">Ready</el-menu-item>
        <el-submenu index="2">
          <template slot="title">Modules</template>
          <el-menu-item v-for="item of 7" :key="item" :index="'2-'+item">Module{{item}}</el-menu-item>
        </el-submenu>
      </el-menu>
    </section>
    <section v-if="currentItem === '1'" class="home">
      <section class="home_title">
        <section class="home_title_p">
          <p>Should you tell people at work about your Mental Health Condition?</p>
        </section>
      </section>
      <section class="home_main">
        <section class="card card_1">
          <p>There is no right or wrong answer when it comes to telling people about your mental health. Each decision is different, and it is important that you think carefully about your options and the affect that it may have on your work and home life.</p>
        </section>
        <section class="card card_2">
          <p>This is a tool that will help inform you about the decision to tell people in your workplace about your mental health condition and help you decide what the best outcome will be for you.</p>
        </section>
        <section class="card card_3">
          <p>At the end you will get a summary of your answers. That may be helpful in making your decision to tell people at work or not.</p>
        </section>
      </section>
      <section class="btn">
        <el-button type="warning" @click="toStart">Start Now<i class="el-icon-arrow-right el-icon--right"></i></el-button>
      </section>
    </section>
    <section v-else>

    </section>
  </div>
</template>

<script>
const titleBg = require('../assets/img/bg_title.jpg');
const homeBg = require('../assets/img/bg_home.jpg')

export default {
  name: "Index",
  data() {
    return {
      currentItem: "1",
      titleBg: titleBg,
      homeBg: homeBg
    }
  },
  methods: {
    itemChange(value) {
      this.currentItem = value;
      console.log(value)
    },
    toStart() {
      this.currentItem = "2-1";
    }
  }
};
</script>
<style scoped>
  .container{
    width: 100%;
    height: auto;
    font-family: "Microsoft YaHei","微软雅黑",Arial,sans-serif;
    overflow: auto;
  }
  .header {
    position: fixed;
    width: 100%;
    padding: 0;
    z-index: 99;
  }
  .el-menu-item, .el-menu--horizontal>.el-submenu /deep/ .el-submenu__title {
    font-size: 28px;
  }
  .el-menu--horizontal .el-menu .el-menu-item{
    float: left;
    margin: 0 10px;
    width: 130px;
    padding: 0;
    font-size: 14px;
    text-align: center;
  }
  .home{
    width: 100%;
    height: 100%;
    margin: 61px auto 0;
    position: relative;
    text-align: center;
  }
  .home_title {
    width: 100%;
    height: 100%;
    background: url('../assets/img/bg_title.jpg') no-repeat;
    background-size: 100%;
    background-position-y: bottom;
  }
  .home_title_p {
    width: 100%;
    height: 100vh;
    background-color :rgba(0,0,0,0.55);
    color: #fff;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    align-content: space-between;
    font-size: 60px;
    text-align: center;
    color: rgba(255,255,255,0.9);
  }
  .home_main {
    width: 100%;
    font-size: 20px;
    text-align: left;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    align-content: center;
  }
  .home_main p{
    margin: 20px 40px;
  }
  .card {
    display: flex;
    width: 400px;
    height: 300px;
    color: #323f4f;
    background-color: #fff;
    align-items: center;
  }
  .card_1 p {
    margin: 20px;
  }
  .card_2 {
    color: #fff;
    background-color: #e89c2c;
  }
  .card_4 {
    width: 50%;
    height: auto;
    top: 200px;
    left: 50%;
    transform: translate(-50%, 0);
    margin-bottom: 20px;
  }
  .home_img {
    width: 100%;
    height: auto;
  }
  .btn {
    position: absolute;
    right: 40px;
    bottom: 10px;
    text-align: right;
  }
  .btn .el-button{
    height: 50px;
    width: 150px;
    font-size: 20px;
  }

  @media screen and (max-width: 379px) {
    .home_title {
      display: inline-block;
      width: 90%;
      margin: 10px auto;
    }
    .home_title_p {
      height: 200px;
      font-size: 20px;
    }
    .home_main {
      font-size: 20px;
      flex-direction: column;
    }
    .home_main p {
      margin: 20px;
    }
    .card {
      width: 90%;
      height: auto;

    }
    .btn {
      position: relative;
      width: 100%;
      margin: 10px 0;
    }
    .btn .el-button{
      margin-right: 20px;
      width: 150px;
      font-size: 20px;
    }
  }
</style>

