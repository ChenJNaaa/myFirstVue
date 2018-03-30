<template>
    <div id="tableList">
      <div class="head">
        <div class="search">
          <input type="text" v-model="uname" placeholder="姓名">
          <button @click="searchForName">查询</button>
        </div>
        <button @click="addUser">新增</button>
      </div>

      <table cellspacing="0" cellpadding="0" >
        <thead>
          <td class="row0">
            <input type="checkbox" v-model:checked="isSelectAll">
          </td>
          <td class="row">序号</td>
          <td class="row">姓名</td>
          <td class="row">性别</td>
          <td class="row">年龄</td>
          <td class="row1">地址</td>
          <td class="row2">操作</td>
        </thead>
        <tr v-for="item in items">
          <td class="row0"><input type="checkbox" v-model:checked="isSelected"></td>
          <td class="row">{{item.id}}</td>
          <td class="row">{{item.name}}</td>
          <td class="row">{{item.sex}}</td>
          <td class="row">{{item.age}}</td>
          <td class="row1">{{item.addr}}</td>
          <td class="row2">
            <button class="edit" @click="goEdit">编辑</button>
            <button class="delete" @click="goDelete">删除</button>
          </td>
        </tr>

      </table>

      <!--新增窗口-->
      <div id="addUser" v-show="isShow">
        <!--<h4>添加</h4>-->
        <div class="title">
          <span>添加</span>
          <i class="iconfont" style="cursor: pointer;" @click="closeAdd">&#xe633;</i>
        </div>
        <div class="addForm" v-model="addForm">
          <div class="name">
            <span>姓名：</span>
            <input type="text" placeholder="姓名" v-model="addForm.name">
          </div>
          <div class="sex" >
            <span>性别：</span>
            <div v-model="addForm.sex" style="display: inline-block">
              <input type="radio" name="sex" value="0" checked="checked">男
              <input type="radio" name="sex" value="1">女
            </div>
          </div>
          <div class="birthday">
            <span>出生日期：</span>
            <input type="date" value="2017-06-01" v-model="addForm.birthday" @input="addAge" >
            <p>年龄是：{{addForm.age}}岁</p>
          </div>
          <div class="address">
            <span>地址：</span>
            <input type="text" placeholder="地址" v-model="addForm.address">
          </div>
        </div>
      </div>

      <div>
        <input type="date" v-model="birthday" @input="getAge" >
        <p>年龄是：{{age}}</p>
      </div>
    </div>
</template>

<script>
/* eslint-disable indent */
    export default {
        name: "table-list",

      data(){
          return {
            uname: '',
            birthday: '',
            age: '',
            isSelectAll: false,
            isSelected: false,
            items: [
              {id: 1, name: 'chen', sex: '男', age: 12, addr: '广东'},
              {id: 2, name: 'chen', sex: '男', age: 12, addr: '广东'},
              {id: 3, name: 'chen', sex: '男', age: 12, addr: '广东'},
              {id: 4, name: 'chen', sex: '男', age: 12, addr: '广东'}
            ],
            isShow: false,
            addForm: {
              name: '',
              sex: -1,
              birthday:'',
              age:'',
              address:'',
            },

          }
      },
      methods:{
          searchForName:function () {
          //  姓名搜索
          },
        addUser:function () {
          //  打开添加用户窗口
          this.isShow = true;
        },
        closeAdd:function () {
          //  关闭添加用户窗口
          this.isShow = false;
        },
        addAge:function () {
          var returnAge;
          var strBirthdayArr = this.addForm.birthday.split("-");
          var birthYear = strBirthdayArr[0];
          var birthMonth = strBirthdayArr[1];
          var birthDay = strBirthdayArr[2];

          var d = new Date();
          var nowYear = d.getFullYear();
          var nowMonth = d.getMonth() + 1;
          var nowDay = d.getDate();

          if (nowYear == birthYear) {
            returnAge = 0;//同年 则为0岁
          }
          else {
            var ageDiff = nowYear - birthYear; //年之差
            if (ageDiff > 0) {
              if (nowMonth == birthMonth) {
                var dayDiff = nowDay - birthDay;//日之差
                if (dayDiff < 0) {
                  returnAge = ageDiff - 1;
                }
                else {
                  returnAge = ageDiff;
                }
              }
              else {
                var monthDiff = nowMonth - birthMonth;//月之差
                if (monthDiff < 0) {
                  returnAge = ageDiff - 1;
                }
                else {
                  returnAge = ageDiff;
                }
              }
            }
            else {
              returnAge = -1;//返回-1 表示出生日期输入错误 晚于今天
            }
          }
          return this.addForm.age = returnAge;
        },
        goEdit:function () {
        //  打开编辑页面
        },
        goDelete:function () {
        //  删除用户
        },
        getAge: function () {
          // alert(this.birthday);
          var returnAge;
          var strBirthdayArr = this.birthday.split("-");
          var birthYear = strBirthdayArr[0];
          var birthMonth = strBirthdayArr[1];
          var birthDay = strBirthdayArr[2];

          var d = new Date();
          var nowYear = d.getFullYear();
          var nowMonth = d.getMonth() + 1;
          var nowDay = d.getDate();

          if (nowYear == birthYear) {
            returnAge = 0;//同年 则为0岁
          }
          else {
            var ageDiff = nowYear - birthYear; //年之差
            if (ageDiff > 0) {
              if (nowMonth == birthMonth) {
                var dayDiff = nowDay - birthDay;//日之差
                if (dayDiff < 0) {
                  returnAge = ageDiff - 1;
                }
                else {
                  returnAge = ageDiff;
                }
              }
              else {
                var monthDiff = nowMonth - birthMonth;//月之差
                if (monthDiff < 0) {
                  returnAge = ageDiff - 1;
                }
                else {
                  returnAge = ageDiff;
                }
              }
            }
            else {
              returnAge = -1;//返回-1 表示出生日期输入错误 晚于今天
            }
          }
          return this.age = returnAge;
        }
      }
    }
</script>

<style scoped>
  @font-face {
    font-family: 'iconfont';  /* project id 606657 */
    src: url('//at.alicdn.com/t/font_606657_cawcp1jci3p4lsor.eot');
    src: url('//at.alicdn.com/t/font_606657_cawcp1jci3p4lsor.eot?#iefix') format('embedded-opentype'),
    url('//at.alicdn.com/t/font_606657_cawcp1jci3p4lsor.woff') format('woff'),
    url('//at.alicdn.com/t/font_606657_cawcp1jci3p4lsor.ttf') format('truetype'),
    url('//at.alicdn.com/t/font_606657_cawcp1jci3p4lsor.svg#iconfont') format('svg');
  }
  .iconfont{
    font-family:"iconfont" !important;
    font-size:20px;font-style:normal;
    -webkit-font-smoothing: antialiased;
    -webkit-text-stroke-width: 0.2px;
    -moz-osx-font-smoothing: grayscale;
    color:#085346;
  }

#tableList{
  margin:0;

  /*
  width: 1280px;
  height: 1020px;
  margin: 30px 0 0 250px;
  float: right;
  background-color: #ffffff;
  border:1px solid #cccccc;
  -webkit-border-radius: 2px;
  -moz-border-radius: 2px;
  border-radius: 2px;
  -webkit-box-shadow: #666 0px 0px 4px;
  -moz-box-shadow: #666 0px 0px 4px;
  box-shadow: #cccccc 0px 0px 4px;
  */

}
.head{
  width:98%;
  height:80px;
  line-height: 80px;
  margin:15px;
  vertical-align: middle;
  background-color: #ccdcdd;
}
.search{
  display: inline-block;
  height: 80px;
  line-height: 80px;
  vertical-align: middle;
  margin-left: 18px;
  margin-top: -3px;
}
.search>input{
  width: 200px;
  height: 40px;
  outline: none;
  font-size: 20px;
  /*margin: auto 10px;*/
  padding-left: 10px;
  border:1px solid #48a386;
  -webkit-border-radius: 2px;
  -moz-border-radius: 2px;
  border-radius: 2px;
  margin-right: 15px;
}
button{
  width: 60px;
  height:40px;
  background-color: #48a386;
  border:1px solid #48a386;
  -webkit-border-radius: 2px;
  -moz-border-radius: 2px;
  border-radius: 2px;
  margin-right: 10px;
  /*border:none;*/
  color:#ffffff;
  font-size: 16px;
  letter-spacing: 0.2em;
}
  .search>button{
    margin-right: 15px;
  }
  table,thead,tr,td{display: inline-block}
  table{
    /*border: 1px solid #cccccc;*/
    /*margin: 15px 0 0 15px;*/
    width:98%;
    margin-top: 15px;
    margin-left: 15px;
    border-collapse:collapse;
  }
  thead{
    background-color: #ccdcdd;
  }
  tr{
    border-bottom: 1px solid #eeeeee;
  }
  table>thead>td,table>tr>td{
    display: inline-block;
    height: 40px;
    line-height: 40px;
    text-align: center;
    /*display: inline-block;*/
  }
  .row0{
    width: 60px;
  }
  .row{
    width: 150px;
  }
  .row1{
    width: 599.2px;
  }
  .row2{
    width: 300px;
  }
  table>tr>td>button{
    width:46px;
    height:28px;
    font-size: 14px;
    border:none;
    letter-spacing: normal;
  }
  .edit{
    background-color: #ffffff;
    border:1px solid #2894ff;
    color: #2894ff;
  }
  .delete{
    background-color: #ffffff;
    border:1px solid #ff5151;
    color:#ff5151;
  }

  #addUser{
    width:800px;
    height:600px;
    -webkit-border-radius: 8px;
    -moz-border-radius: 8px;
    border-radius: 8px;
    -webkit-box-shadow: #666 0px 0px 10px;
    -moz-box-shadow: #666 0px 0px 10px;
    box-shadow: #cccccc 0px 0px 10px;
    background-color: #ffffff;
    position: fixed;
    margin-left:300px;
    margin-top:-300px;
  }
  .title{
    width:760px;
    height:40px;
    line-height: 40px;
    margin: 20px auto;
  }
  .title span{
    color: #085346;
    font-size: 18px;
  }
  .title i{
    float: right;
  }
  .addForm{
    width:760px;
    height:300px;
    margin:0 auto;
    color: #085346;
    font-size: 18px;
  }
  .addForm div{
    margin:15px 0;
  }
  .name{
    height:40px;
    line-height: 40px;
  }
  .name input,.birthday input,.birthday input,.address input{
    width: 300px;
    height: 30px;
    line-height: 30px;
    font-size: 14px;
    outline:none;
    /*border:none;*/
    border:1px solid #48a346;
    padding:0 8px;
    -webkit-border-radius: 2px;
    -moz-border-radius: 2px;
    border-radius: 2px;
  }
  .birthday input{
    width:150px;
    /*color: #999999;*/
  }
  .address input{
    width:450px;
  }
</style>
