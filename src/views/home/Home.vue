<template>
  <div id="home" class="wrapper">
    <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
      
      <home-swiper :banners="banners"/>
      <recommend-view :recommends="recommends"/>
      <feature-view></feature-view>
      <tab-control class="tab-control" 
      :titles="['流行','新款','精选']" 
      @tabClick="tabClick">
      </tab-control>
      <good-list :goods="goods[currentType].list"></good-list>
    <!-- //事件监听整个组件的时候用原生属性native -->
    <!-- <back-top @click.native="topClick"></back-top> -->
  </div>
</template>

<script>
  
  import HomeSwiper from './childComps/HomeSwiper'
  import RecommendView from './childComps/RecommendView'
  import FeatureView from "./childComps/FeatureView.vue"

  import NavBar from '../../components/common/nvabar/NavBar'
  import TabControl from '../../components/content/tabControl/TabControl'
  import GoodList from '../../components/content/goods/GoodsList'
  import {getHomeMultidata,getHomeGoods} from "../../network/home"

  // import BackTop from '../../components/content/backTop/BackTop'
  
  export default {
    name: "Home",
    components: {
      HomeSwiper,
      RecommendView,
      FeatureView,
      NavBar,
      TabControl,
      GoodList,
      // BackTop

      
    },
    data() {
      return {
        //保存数据
        banners: [],
        recommends: [],
        goods: {
          'pop': {page: 0, list: []},
          'new': {page: 0, list: []},
          'sell': {page: 0, list: []},
        },
        currentType: 'pop',
      }
     
    },

    computed: {
		  showGoods() {
		    return this.goods[this.currentType].list
      }
    },
    //生命周期函数
    created() {
      // 1.请求多个数据
      this.getHomeMultidata()

      // 2.请求商品数据
      this.getHomeGoods('pop')
      this.getHomeGoods('new')
      this.getHomeGoods('sell')

    },
    
    methods:{
      // 事件监听相关的方法
      tabClick(index) {
		    switch (index) {
          case 0:
            this.currentType = 'pop'
            break
          case 1:
            this.currentType = 'new'
            break
          case 2:
            this.currentType = 'sell'
            break
        }
        
      },

      topClick(){
        // this.$refs.scroll.scrollTo(0,0,500)
        //回到顶部
        var scrolltop = document.documentElement.scrollTop || document.body.scrollTop;
        document.documentElement.scrollTop = document.body.scrollTop =0;  
        // console.log(scrolltop);
      },

      // 网络请求相关的方法
      getHomeMultidata() {
        getHomeMultidata().then(res => {
          this.banners = res.data.banner.list;
          this.recommends = res.data.recommend.list;
        })
      },
      getHomeGoods(type) {
        //请求页数
        const page = this.goods[type].page + 1
        //拿到请求的页数
        getHomeGoods(type, page).then(res => {
          //将数组list里的数据拿到上面的list中，语法就是push（...list）
          this.goods[type].list.push(...res.data.list)
          //页数加1
          this.goods[type].page += 1
        })
      }
    }
  }
</script>


<style scoped>
/*  scoped表示内部的样式仅对当前有效 */
  #home{
    padding-top:44px;
    height: 100vh; 
    position: relative
  }

  .home-nav {
    background-color: var(--color-tint);
    color: #fff;

    position: fixed;
    left: 0;
    right: 0;
    top: 0;
    z-index: 9;
  }
  
  .content {
    position: absolute;
    top: 44px;
    bottom: 49px;
    left: 0;
    right: 0;
  }

  .tab-control{
    position: sticky;
    top: 44px;
    /* z-index: 11; */
  }
</style>
