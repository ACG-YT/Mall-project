<template>
    <div id='app'>
      <nav-bar class="nav-bar"><div slot="center">购物车({{cartCount}})</div></nav-bar>
      <cart-list class="cart-list" :cart-list="cartList"></cart-list>
      <bottom-bar></bottom-bar>
    </div>
</template>

<script>
  import NavBar from '../../components/common/nvabar/NavBar'
  import BottomBar from './childComps/BottomBar.vue'
  import CartList from './childComps/CartList'



  export default {
    name: "Cart",
    components:{
      NavBar,
      CartList,
      BottomBar
      
    },
    computed:{
      cartList(){
        return this.$store.getters.cartList
      },
      cartCount(){
        return this.$store.getters.cartCount
      }
    }
  }
</script>

<style scoped>
  #cart {
    /*position: relative;作为cartList的父组件需要有自己的高度，这也是cal使用的前提*/
    height: 100vh;
  }

  .nav-bar {
  background-color: var(--color-tint);
  color: #fff;
  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  z-index: 9;
  }

  .cart-list {
    position: absolute;
    top: 44px;
    bottom: 49px;
    width: 100%;
  }
</style>
