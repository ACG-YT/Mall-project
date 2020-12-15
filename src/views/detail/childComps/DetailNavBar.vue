<template>
  <div id="detail">
      <nav-bar>
        <div slot="left" class="back" @click="backClick">
            <img src="../../../assets/img/common/back.svg" alt="">
        </div>
          <div slot="center" class="title">
            <div v-for="(item,index) in titles" 
            class="title-item" 
            :class="{active:index==currentIndex}" @click="titleClick(index)" >
            {{item}}</a></div>
          </div>
        </nav-bar>
  </div>
</template>

<script>
import NavBar from '../../../components/common/nvabar/NavBar'

  export default {
    name: "DetailNarBar",
    components:{
        NavBar
    },
    data(){
      return{
        titles:['店铺','商品','参数'],
        currentIndex:0
      }
    },
    methods:{
      titleClick(index){
        this.currentIndex = index
      },
      backClick(){
        this.$router.back()
      }
    }
  }
</script>

<style scoped>
.title{
  display: flex;
  font-size: 14px;
}

.title-item{
  flex: 1;
}

/* .active{
  color: var(--color-high-text);
} */

.back img{
  margin-top: 12px;
}

.nav-bar {
    background-color: #fff;
position: fixed;
left: 0;
right: 0;
top: 0;
z-index: 9;
  }
</style>
