<template>
  <div id="app">
    <div class="header">
      <h1>My Shop</h1>
    </div>
    <Cart ref="cartComp" :cartItems="cartItems"/>
    <Products :pList="pList" @addProductToCart="addProductToCart"/>
  </div>
</template>

<script>
import Cart from './components/Cart';
import Products from './components/Products';
const uuid = require('uuid');
const cartItems = [
  // { name: "product1", id: 1, price: 30, qu: 1 },
  // { name: "product2", id: 2, price: 20, qu: 3 },
  // { name: "product3", id: 3, price: 10, qu: 2 }
];
const pList = [
  {name: 'Apple-Tv', price: '200', id: uuid()},
  {name: 'Radio', price: '150', id: uuid()},
  {name: 'PC', price: '1000', id: uuid()},
  {name: 'MAC', price: '1200', id: uuid()},
  {name: 'Table', price: '200', id: uuid()},
  {name: 'Food', price: '150', id: uuid()},
  {name: 'Desk', price: '1000', id: uuid()},
  {name: 'Kitchen', price: '1200', id: uuid()},
]

export default {
  name: "app",
  components: {Cart, Products},
  data() {
    return {
      cartItems,
      pList
    };
  },
  methods:{
    addProductToCart: function(product){
      const item = {
        name: product.name,
        price: product.price,
        id: product.id,
        qu:1
      }
      this.$refs.cartComp.addCartItem(item);
    }
  }
};
</script>


<style lang="less">
#app {
  font-family: Arial, Helvetica, sans-serif;
  width: 50%;
  margin: 0 auto;
}
</style>