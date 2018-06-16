<template>
  <div id="app">
    <div class="header">
      <h1>My Shop</h1>
    </div>
    <Cart :cartItems="cartItems"/>
  </div>
</template>

<script>
import Cart from './components/Cart';
const cartItems = [
  { name: "product1", id: 1, price: 30, qu: 1 },
  { name: "product2", id: 2, price: 20, qu: 3 },
  { name: "product3", id: 3, price: 10, qu: 2 }
];
export default {
  name: "app",
  components: {Cart},
  data() {
    return {
      cartItems
    };
  }
};
</script>


<style lang="less">
#app {
  font-family: Arial, Helvetica, sans-serif;
}
</style>