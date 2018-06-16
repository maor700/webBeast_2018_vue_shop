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
  .price {
    margin: 0 1em;
  }
  .cart-table {
    margin: 0 auto;
    width: 50%;
    text-align-last: left;
    .table-header,
    .table-footer,
    .cart-items > .item {
      border: 1px solid gray;
      padding: 0.3em;
      display: flex;
      .name {
        flex: 50;
      }
      .price,
      .qu {
        flex: 25;
      }
    }

    .cart-items > .item {
      .qu {
        display: flex;
        justify-content: space-around;
      }
    }
    .table-header {
      background-color: black;
      color: white;
      font-weight: bold;
    }
  }
}
</style>