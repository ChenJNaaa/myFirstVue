<template>
    <div id="navbar">
      <div class="left">
        <ul>
          <li>导航一
            <i class="iconfontRight" @click="start">&#xe615;</i>
            <ul>
              <li>下拉菜单1</li>
              <li>下拉菜单2</li>
            </ul>
          </li>
          <li>导航二</li>
          <li>导航三</li>
          <li>导航四</li>
          <li>导航五</li>
        </ul>
      </div>
    </div>
</template>

<script>
  /* eslint-disable indent */
    export default {
      name: "Navbar",
      methods: {
        start () {
          this.rotate=!this.rotate;
          console.log(this.rotate)
        }
      }
    }
</script>

<style scoped>
  @font-face {
    font-family: 'iconfont';  /* project id 606657 */
    src: url('//at.alicdn.com/t/font_606657_cvjnryg1um9dlsor.eot');
    src: url('//at.alicdn.com/t/font_606657_cvjnryg1um9dlsor.eot?#iefix') format('embedded-opentype'),
    url('//at.alicdn.com/t/font_606657_cvjnryg1um9dlsor.woff') format('woff'),
    url('//at.alicdn.com/t/font_606657_cvjnryg1um9dlsor.ttf') format('truetype'),
    url('//at.alicdn.com/t/font_606657_cvjnryg1um9dlsor.svg#iconfont') format('svg');
  }
  .iconfontRight{
    font-family:"iconfont" !important;
    font-size:12px;font-style:normal;
    -webkit-font-smoothing: antialiased;
    -webkit-text-stroke-width: 0.2px;
    -moz-osx-font-smoothing: grayscale;
    float: right;
    transform:rotate(-180deg);
  }

  #navbar{
    margin:0;
    width: 220px;
    display: inline-block;
    float: left;
  }
  .left{
    margin:0;
    width:220px;
    height: 1000px;
    border-right: 1px solid #085346;
    background-color: rgb(238,241,246);
  }

  .left ul{
    margin:0;
    padding:0;
    list-style: none;
  }
  .left>ul>li{
    display: inline-block;
    padding: 0 20px;
    width: 180px;
    height: 56px;
    line-height: 56px;
    font-size: 16px;
    color: #085346;
  }
  .left>ul>li:hover{
    background-color: rgb(209,219,229);
    border-bottom: 1px solid #085346;
  }
  .left>ul>li:hover .iconfontRight{
    transition: all 0.4s;
    transform:rotate(0deg);
   }
  .left>ul>li>ul{
    display:none;
    padding:0;

  }
  .left>ul>li:hover ul {
    display: inline-block;
  }

  .left>ul>li:hover ul li{
    width: 180px;
    height: 40px;
    line-height: 40px;
    padding: 0 15px 0 5px;
    color: #288366;
    margin:0;
   }
  .left>ul>li>ul>li:hover{
    color: yellowgreen;
  }

</style>
