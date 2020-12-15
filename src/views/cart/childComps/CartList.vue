<template>
  <!-- <scroll class="contet"> -->
    <div>
      <cart-list-item v-for="item in cartList" :key="item.iid" :item-info="item"></cart-list-item>
    </div>
  <!-- </scroll> -->
</template>

<script>
  // import Scroll from '../../../components/common/scroll/Scroll'
  import CartListItem from './CartListItem'

	export default {
		name: "CartList",
    components: {
      // Scroll, 
      CartListItem
    },
    // props: {s
		//   cartList: {
		//     type: Array,
    //     default() {
		//       return []
    //     }
    //   }
    // },
    computed:{
      cartList(){
        return this.$store.getters.cartList
      }
    }
	}
</script>

<style scoped>
.cart-list{
  height: calc(100% - 44px - 49px);
}

.contet{
  height: 100%;
  overflow: hidden;
}
</style>
