<template>
	<div class="my-cart-con">
  <div class="cart-table">
    <div class="table-header">
      <div class="name">name</div>
      <div class="qu">qu</div>
      <div class="price">price</div>
      <div class="remove">remove</div>
    </div>
    <div class="cart-items">
    <div class="item" v-for="item in cartItems" :key="item.id">
      <span class="name">{{item.name}}</span>
      <div class="qu">
        <button @click="()=>{item.qu--}">-</button>
        <span>{{item.qu}}</span>
        <button @click="()=>{item.qu++}">+</button>
        </div>
      <span class="price">{{item.price}}$</span>
	  <div @click="removeCartItem(item.id)" class="remove">X</div>
    </div>
    <div class="table-footer">
      <div class="name"></div>
      <div class="qu">{{calcTotalQu}}</div>
      <div class="price">{{calcTotalPrice}}$</div>
      <div class="remove"> </div>
    </div>
    </div>
	<button @click="addCartItem({ name: 'product3', id: 3, price: 10, qu: 2 })"> Add Item</button>
	<button @click="removeCartItem(3)"> Remove Item</button>
  </div>
</div>
</template>


<script>
const uuidv1 = require('uuid/v1');

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
      return this.cartItems.length && this.cartItems
        .map(item => {
          return item.price * item.qu;
        })
        .reduce((total, currentval) => {
          return total + currentval;
        });
    },
    calcTotalQu: function() {
      let total = 0;
      return this.cartItems.length && this.cartItems
        .map(item => {
          return item.qu;
        })
        .reduce((total, currentval) => {
          return total + currentval;
        });
    }
  },
  methods: {
	  addCartItem: function(item){
		  item.id = uuidv1();
		  this.cartItems.push(item);
	  },
	  removeCartItem: function(id) {
		  const index = this.cartItems.findIndex((item)=>{
			  return item.id == id;
		  });
		  (index != -1) && this.cartItems.splice(index,1);
	  }
  }

}
</script>

<style lang="less">

</style>
