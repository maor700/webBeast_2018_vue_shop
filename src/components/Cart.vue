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
    		<CartItem class="item" v-for="item in cartItems" :key="item.id" :item="item" @removeCartItem="removeCartItem($event)"/>
    <div class="table-footer">
      <div class="name"></div>
      <div class="qu">{{calcTotalQu}}</div>
      <div class="price">{{calcTotalPrice}}$</div>
      <div class="remove"> </div>
    </div>
    </div>
	<button @click="addCartItem({ name: 'product3', id: 3, price: 10, qu: 2 })"> Add Item</button>
  </div>
</div>
</template>


<script>
import CartItem from "./CartItem";
const uuidv1 = require("uuid/v1");

export default {
  name: "Cart",
  props: ["cartItems"],
  components: { CartItem },
  data() {
    return {};
  },
  computed: {
    calcTotalPrice: function() {
      let total = 0;
      return (
        this.cartItems.length &&
        this.cartItems
          .map(item => {
            return item.price * item.qu;
          })
          .reduce((total, currentval) => {
            return total + currentval;
          })
      );
    },
    calcTotalQu: function() {
      let total = 0;
      return (
        this.cartItems.length &&
        this.cartItems
          .map(item => {
            return item.qu;
          })
          .reduce((total, currentval) => {
            return total + currentval;
          })
      );
    }
  },
  methods: {
    addCartItem: function(item) {
      item.id = uuidv1();
      this.cartItems.push(item);
    },
    removeCartItem: function(id) {
      const index = this.cartItems.findIndex(item => {
        return item.id == id;
      });
      index != -1 && this.cartItems.splice(index, 1);
    }
  }
};
</script>

<style lang="less">
</style>
