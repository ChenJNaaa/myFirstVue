<template>
    <div id="regist" @keyup.enter="regist" v-cloak>
      <div novalidate="novalidate" autocomplete="off">
        <div class="registBox" style="margin-top: 60px">
          <span>用户名:</span>
          <input v-model="username" type="text" placeholder="用户名" required>
        </div>
        <div class="registBox">
          <span>密码:</span>
          <input v-model="password" type="password" placeholder="密码" required>
        </div>
        <div class="registBox" style="margin-bottom: 30px">
          <span>确认密码:</span>
          <input v-model="repassword" type="password" placeholder="再输入一次密码" required>
        </div>
        <!--<button style="margin-right: 20px;" v-on:click="login">登录</button>-->
        <button v-on:click="regist">注册</button>
        <span class="loginTip">已有账号<a href="/login" >登录</a></span>
      </div>
    </div>
</template>

<script>
/* eslint-disable indent */

    export default {
      name: 'Regist',
      data () {
        return {
          username:'',
          password:'',
          repassword:'',
        }
      },
      computed: {
      },
      methods: {

        isEmpty(val){
          return val === '';
        },
        isValidUserName(val){
          return /^[a-aA-Z0-9_]+$/.test(val);
        },
        isValidPassword(val){
          return /^[A-Za-z0-9_]{4,}$/.test(val);
        },
        check(obj){
          if(this.isEmpty(obj.username)){
            alert('用户名不能为空！');
            // this.openDialog('check');
            return false;
          }if(this.isEmpty(obj.password)){
            alert('密码不能为空！');
            // this.openDialog('check');
            return false;
          }if(this.isEmpty(obj.repassword)){
            alert('确认密码不能为空！');
            // this.openDialog('check');
            return false;
          }if(!this.isValidUserName(obj.username)){
            alert('用户名不能含有除字母或数字或下划线的任何字符');
            this.openDialog('check');
            return false;
          }if(!this.isValidPassword(obj.password)){
            alert('密码必须是至少4位的字母或数字组合');
            // this.openDialog('check');
            return false;
          }if(!this.isValidPassword(obj.repassword)){
            alert('密码必须是少于4位的字母或数字组合');
            // this.openDialog('check');
            return false;
          }
          return true;
        },
        doneRegist(){
          this.alert.content = '注册成功';
          this.alert.ok = '';
          this.openDialog('check');
        },
        openDialog(ref){
          this.$refs[ref].open();
        },
        closeDialog(ref){
          this.$refs[ref].close();
        },

        /*
        regist(){
          var username = this.username;
          var password = this.password;
          var repassword = this.repassword;
          if(!this.check({
              username: username;
              password: password;
              repassword: repassword;
            }))return;
          this.registing = true;
          var user = new AV.User();
          user.setUsername(username);
          user.setPassword(password);
          user.signUp().then(function(loginedUser){
            this.registing = false;
            this.doneRegist();
            setTimeout(function(){
              this.$router.push({
                name: 'home'
              })
            }.bind(this),600)
          }.bind(this),(function(error){
            if(error.code = '202'){
              this.alert.content = '用户名已存在';
            }else {
              this.alert.content = '注册失败，请重试';
            }
            this.openDialog('check');
            this.registing = false;
          }.bind(this)));
        }

        */

        regist () {

          var username = this.username;
          var password = this.password;
          var repassword = this.repassword;
          /*验证用户名和密码是否为空*/
          if (!this.check({
              username: username,
              password: password
            }))return;
          alert(this.check({
            username: username,
            password: password
          }));
          if(password === repassword){
            alert('注册成功');
          }else{
            alert('注册失败');
          }
        }
      }



      /*
      goLogin () {
        this.$router.push({
          name: 'Login'
        });
      },
     */
    }
</script>

<style scoped>
  #regist{
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

  .registBox{
    width: 400px;
    height: 60px;
    line-height: 60px;
    margin:15px auto;
    vertical-align: middle;
  }

  .registBox span{
    display: inline-block;
    width: 6rem;
    height: 30px;
    line-height: 30px;
    text-align: right;
    color: #085346;
  }

  .registBox input{
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
  button {
    width: 50px;
    height: 36px;
    border: none;
    background-color: #085346;
    color: #ffffff;
    font-size: 16px;
    vertical-align: center;
  }
  .loginTip{
    display: inline-block;
    margin-left: 40px;
    font-size: 12px;
  }
  a{
    color: red;
    text-decoration: red;
    /*cursor: pointer;*/
    font-size: 12px;
  }
</style>
