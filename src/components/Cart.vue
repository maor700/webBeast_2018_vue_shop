<template>
	<div class="my-cart-con">
  <div class="cart-table">
    <div class="table-header">
      <div class="name">name</div>
      <div class="qu">qu</div>
      <div class="price">price</div>
    </div>
    <div class="cart-items">
    <div class="item" v-for="item in cartItems" :key="item.id">
      <span class="name">{{item.name}}</span>
      <div class="qu">
        <button @click="()=>{item.qu--}">-</button>
        <span>{{item.qu}}</span>
        <button @click="()=>{item.qu++}">+</button>
        </div>
      <span class="price">{{item.price * item.qu}}$</span>
    </div>
    <div class="table-footer">
      <div class="name"></div>
      <div class="qu">{{calcTotalQu}}</div>
      <div class="price">{{calcTotalPrice}}</div>
    </div>
    </div>
  </div>
</div>
</template>


<script>
export default {
	name: "Cart",
	props: ["cartItems"],
	data(){
		return {

		}
	},
	computed: {
    calcTotalPrice: function() {
      let total = 0;
      return this.cartItems
        .map(item => {
          return item.price * item.qu;
        })
        .reduce((total, currentval) => {
          return total + currentval;
        });
    },
    calcTotalQu: function() {
      let total = 0;
      return this.cartItems
        .map(item => {
          return item.qu;
        })
        .reduce((total, currentval) => {
          return total + currentval;
        });
    }
  }

}
</script>

<style lang="less">

</style>
