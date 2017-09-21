<template>
  <div id="topbar">
    <div class="logo">
      <img src="../assets/logo.png" alt="">
      <h1>VueResume</h1>
    </div>
    <div class="actions">
      <el-button type="success">注册</el-button>
      <el-button :plain="true" type="success">登录</el-button>
    </div>
  </div>
</template>

<style lang="scss">
  #topbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem;
    .logo{
      display: flex;
      align-items: center;
      img{
        height: 5rem;
      }
      h1{
        font-size: 3rem;
      }
    }
    .actions{

    }
  }
</style>
