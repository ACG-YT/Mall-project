<template>
  <div id="profile">
    <nav-bar class="nav-bar"><div slot="center">我的商城</div></nav-bar>
    
    <div class="info">
      <img src="../../assets/img/profile/avatar.svg">
      <div class="center">
        <span>登录/注册</span>
        <p>暂无绑定手机号</p>
      </div>
    </div>

    <div class="detail">
      <div class="left">
        <p>0.00元</p>
        <span>我的余额</span>
      </div>
      <div class="left">
        <p>0个</p>
        <span>我的优惠</span>
      </div>
      <div class="left">
        <p>0分</p>
        <span>我的积分</span>
      </div>
    </div>

    <div class="news">
      <div class="news_news">
        <img src="../../assets/img/profile/message.svg">
        <span>我的消息</span>
      </div>
       <div class="news_news">
        <img src="../../assets/img/profile/pointer.svg">
        <span>积分商城</span>
      </div>
       <div class="news_news">
        <img src="../../assets/img/profile/vip.svg">
        <span>会员卡</span>
      </div>
    </div>

    <div class="cart">
      <div class="my_cart">
        <img src="../../assets/img/profile/cart.svg">
        <span>我的购物车</span>
      </div>
      <div class="download">
        <img src="../../assets/img/profile/shopping.svg">
        <span>下载购物APP</span>
      </div>
    </div>
  </div>
</template>

<script>
import NavBar from '../../components/common/nvabar/NavBar'
  export default {
    components:{
      NavBar
    }
}
</script>

<style scoped>
.cart{
  width: auto;
  height: 88px;
  margin-top: 15px;
  background-color: #fff;
}
.my_cart{
    width: auto;
  height: 44px;
  line-height: 44px;
  padding-left: 10px;
  background-color: #fff;
  border-bottom: 1px solid #eee;
}
.my_cart img{
  width: 30px;
  height: 40px;
  float: left;
}

.download{
  width: auto;
  height: 44px;
  line-height: 44px;
  padding-left: 10px;
  background-color: #fff;
  border-bottom: 1px solid #eee;
}
.download img{
  width: 30px;
  height: 40px;
  float: left;
}

  #profile { 
    background-color: #f2f2f2;

  }

  .nav-bar {
    background-color: var(--color-tint);
    font-weight: 700;
    color: #fff;
  }

.info{
  width: auto;
  height: 90px;
  padding: 15px;
  background-color: var(--color-tint);
  margin: 0 auto
}

.info img{
  height: 60px;
  width: 60px;
  background-color: #fff;
  border-radius: 30px;
  float: left;
}

.info .center{
  color: #fff;
  margin: 10px 0 0 30px;
  width: 200px;
  height: 50px;
}

.info .center span{
  padding-left: 20px;
}

.info .center p{
  padding-left: 50px;
}

.detail{
  width: auto;
  height: 84px;
  background: #fff;
  margin: 0 auto;
}
.detail .left{
  width: 124px;
  height: 84px;
  padding: 18px;
  text-align: center;
}
.detail .left p{
  padding-bottom: 3px;
  color: var(--color-tint);
}

.news{
  width: auto;
  height: 123px;
  margin-top: 5px;
  background-color: #fff;
  
}

.news_news{
  width: auto;
  height: 44px;
  line-height: 44px;
  padding-left: 10px;
  background-color: #fff;
  border-bottom: 1px solid #eee;
}

.news_news img{
  width: 30px;
  height: 40px;
  float: left;
}

.news_news span{
  margin-left: 10px;
}


</style>