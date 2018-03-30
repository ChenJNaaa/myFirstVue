<template>
    <div id="header">
      <p>MyFirstVue</p>
      <div class="user">
        <span>亲爱的<a @click="showList">{{this.username}}</a>欢迎光临~</span>
        <a @click="logout">退出登录</a>
      </div>
    </div>
</template>

<script>
  /* eslint-disable indent */
    export default {
        name: "Header",
      data () {
          return {
            username: ''
          }
      },
      methods: {
          showList:function () {
          },
          logout: function () {
            var isLogout = confirm('确认退出吗？');
            if(isLogout){
              this.$router.push({path: '/login'});
            }else {
              this.$router.push('/home');
            }
          }
      }
    }
</script>

<style scoped>
#header{
  width: 100%;
  height: 80px;
  background-color: #085346;
}
#header>p {
  margin: 0;
  width: 220px;
  height: 80px;
  line-height: 80px;
  text-align: center;
  font-size: 20px;
  color: #ffffff;
  float: left;
  border-right: 1px solid #fffbbd;
}
  .user{
    /*width:160px;*/
    height:80px;
    float: right;
    vertical-align: middle;
    margin-right: 30px;
    font-size: 14px;
  }
  .user>span{
    display: inline-block;
    height:80px;
    line-height: 80px;
    color:#ffffff;
    margin-right: 15px;
  }
  .user>a{
    color: aquamarine;
  }
</style>
