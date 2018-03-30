<template>
  <div id="home" v-cloak>
    <div class="header"><Header></Header></div>
    <div class="navbar"><Navbar></Navbar></div>
    <!--<Header></Header>-->

    <!--<TableList></TableList>-->
    <div class="main"><TableList></TableList></div>
  </div>
</template>

<script>
/* eslint-disable indent */
import Header from "./section/Header.vue"
import Navbar from "./section/Navbar.vue"
import TableList from "./content/TableList"

    export default {
      name: 'home',
      components: {
        Navbar,
        Header,
        TableList
      },
      data () {
        return{}
      },
      computed: {
      },
      methods: {
      }
    }
</script>

<style scoped>
#home{
  padding:0;
  margin:0;
}
.header{
  width: 100%;
  height: 80px;
}
.navbar{
  width: 220px;
  height: 100%;
}
.main{
  width:1620px;
  height: 960px;
  margin-top: 40px;
  margin-right: 15px;
  float: right;
  background-color: #ffffff;
  border:1px solid #cccccc;
  -webkit-border-radius: 2px;
  -moz-border-radius: 2px;
  border-radius: 2px;
  -webkit-box-shadow: #666 0px 0px 4px;
  -moz-box-shadow: #666 0px 0px 4px;
  box-shadow: #cccccc 0px 0px 4px;
}
</style>
