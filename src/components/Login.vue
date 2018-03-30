<template>
    <div id="login" @keyup.enter="login" v-cloak>
      <div novalidate="novalidate" autocomplete="off">
        <div class="loginBox" style="margin-top: 60px">
          <!--<span>用户名:</span>-->
          <i class="iconfont">&#xe60a;</i>
          <input v-model="username" type="text" placeholder="用户名" required>
        </div>
        <div class="loginBox" style="margin-bottom: 30px">
          <!--<span>密码:</span>-->
          <i class="iconfont">&#x85346;</i>
          <input v-model="password" type="password" placeholder="密码" required>
        </div>
        <button style="margin-right: 20px;" v-on:click="login">登录</button>
        <button v-on:click="goRegist">注册</button>
      </div>
    </div>
</template>

<script>
  /* eslint-disable indent */

  export default {
    name: 'Login',
    data () {
      return {
        username: '',
        password: ''
      }
    },
    computed: {
    },

    /*
    great: function () {
      return this.name
    },
    */

    methods: {
      login: function () {
        var username = this.username;
        var password = this.password;
        if(username === 'test'){
          if(password === 'test'){
            alert('登录成功~');
            this.$router.push({path:'/home'})
          }else{
            alert('密码错误！');
            alert('密码错误！');
          }
        }else {
          alert('用户名错误！');
        }
      },
      goRegist: function () {
        this.$router.push({
          name:'Regist'
        })
      }
    }

  }

</script>

<style scoped>

  @font-face {
    font-family: 'iconfont';  /* project id 606657 */
    src: url('//at.alicdn.com/t/font_606657_sbri6sm99k162yb9.eot');
    src: url('//at.alicdn.com/t/font_606657_sbri6sm99k162yb9.eot?#iefix') format('embedded-opentype'),
    url('//at.alicdn.com/t/font_606657_sbri6sm99k162yb9.woff') format('woff'),
    url('//at.alicdn.com/t/font_606657_sbri6sm99k162yb9.ttf') format('truetype'),
    url('//at.alicdn.com/t/font_606657_sbri6sm99k162yb9.svg#iconfont') format('svg');
  }

  .iconfont{
    font-family:"iconfont" !important;
    font-size:28px;font-style:normal;
    -webkit-font-smoothing: antialiased;
    -webkit-text-stroke-width: 0.2px;
    -moz-osx-font-smoothing: grayscale;
    color:#085346;
  }

  #login{
    border:1px solid #dddddd;
    width:600px;
    height:400px;
    margin:50px auto;
    text-align: center;
    vertical-align: middle;
    font-family: "微软雅黑";
    font-size: 16px;
    -webkit-border-radius: 8px;
    -moz-border-radius: 8px;
    border-radius: 8px;
    -webkit-box-shadow: #666 0px 0px 10px;
    -moz-box-shadow: #666 0px 0px 10px;
    box-shadow: #cccccc 0px 0px 10px;
  }
  .loginBox{
    width: 400px;
    height: 60px;
    line-height: 60px;
    margin:15px auto;
    vertical-align: middle;
  }
  /*
  .loginBox span{
    width: 4rem;
    height: 30px;
    line-height: 30px;
    text-align: center;
    color: #f4cdde
  }
  */
  .loginBox input{
    display: inline-block;
    width: 200px;
    heigth: 32px;
    margin-left: 15px;
    border: none;
    border-bottom: 1px solid #085346;
    outline:none;
    /*cursor: pointer; //获取焦点时光标呈现为指示链接的指针（一只手）*/
    font-size: 16px;
  }
  button{
    width:50px;
    height:36px;
    border:none;
    background-color: #085346;
    color: #ffffff;
    font-size: 14px;
  }
</style>
