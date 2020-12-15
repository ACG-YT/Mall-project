<template>
  <div id="detail">
      <detail-nav-bar class="detail-nav"></detail-nav-bar>
      <!-- <scroll class="content"> -->
        <detail-swiper :top-images="topImages"></detail-swiper>
        <detail-base-info :goods="goods"></detail-base-info>
        <detail-shop-info :shop="shop"></detail-shop-info>
        <detail-goods-info :detail-info="detailInfo"></detail-goods-info>
        <detail-param-info :param-info="paramInfo"></detail-param-info>
        <!-- <detail-comment-info :comment-info="commentInfo"></detail-comment-info> -->
        <goods-list :goods="recommends"></goods-list>
      <!-- </scroll> -->
      <detail-bottom-bar @addToCart="addToCart"></detail-bottom-bar>
  </div>
</template>

<script>
import DetailNavBar from './childComps/DetailNavBar'
import DetailSwiper from './childComps/DetailSwiper'
import DetailBaseInfo from './childComps/DetailBaseInfo'
import DetailShopInfo from './childComps/DetailShopInfo'
import DetailGoodsInfo from './childComps/DetailGoodsInfo'
import DetailParamInfo from './childComps/DetailParamInfo'
// import DetailCommentInfo from './childComps/DetailCommentInfo'
import GoodsList from '../../components/content/goods/GoodsList'

// import Scroll from '../../components/common/scroll/Scroll'
import {getDetail,Goods,Shop,GoodsParam,getRecommend} from '../../network/detail'


import DetailBottomBar from './childComps/DetailBottomBar'


  export default {
    name: "Detail",
    components:{
        DetailNavBar,
        DetailSwiper,
        DetailBaseInfo,
        DetailShopInfo,
        // Scroll,
        DetailGoodsInfo,
        DetailParamInfo,
        // DetailCommentInfo,
        GoodsList,
        DetailBottomBar
        
    },
    data(){
        return{
          iid:null,
          topImages:[],
          goods:{},
          shop:{},
          detailInfo:{},
          paramInfo:{},
          // commentInfo:{},
          recommends:[]
        }
    },

    methods:{
        addToCart(){
          // 获取需要展示的信息
          const obj = {}
        // 2.对象信息
        obj.iid = this.iid;
        obj.imgage = this.topImages[0]
        obj.title = this.goods.title
        obj.desc = this.goods.desc;
        obj.newPrice = this.goods.nowPrice;

        // 3.添加到Store中
        this.$store.commit('addCart', obj)
        }
    },
    created(){
        //1、保存iid
        this.iid = this.$route.params.id;

        // 2、根据iiid请求详情数据
        getDetail(this.iid).then(res => {
          console.log(res);
          // 2.1、获取结果
          const data = res.result;

          // 2.2、获取轮播图片数据
          this.topImages = data.itemInfo.topImages

          // 2.3、获取商品数据
          this.goods = new Goods(data.itemInfo,data.columns,data.shopInfo.services)

          //2.4获取店铺信息
          this.shop = new Shop(data.shopInfo)

          //2.5获取商品详情信息
          this.detailInfo = data.detailInfo

          //2.6获取参数信息
          this.paramInfo = new GoodsParam(data.itemParams.info,data.itemParams.rule)

          //2.7取出评论的信息
          // if(data.rate.cRate !== 0){
          //   this.commentInfo = data.rate.list[0]
          // }
        })

        //3.请求推荐数据
        // getRecommend().then(res => {
        //   console.log(res);
        //     this.recommends = res.data.list
        // })



    }
  }
</script>

<style scoped>
  #detail {
    position: relative;
    z-index: 9;
    background-color: #fff;
  }

  .detail-nav{
    position: relative;
    z-index: 9;
  }


  .content{
    height: calc(100% - 44px);
  }

 
 
</style>
