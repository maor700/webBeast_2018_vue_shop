<template>
    <div>
      <span class="name">{{item.name}}</span>
      <div class="qu">
        <button @click="downQu(item)">-</button>
        <span>{{item.qu}}</span>
        <button @click="upQu(item)">+</button>
        </div>
      <span class="price">{{item.price}}$</span>
	  <div @click="$emit('removeCartItem', item.id)" class="remove">X</div>
    </div>
</template>

<script>
export default {
  name: "CartItem",
  props: ["item"],
  methods: {
    upQu: function(item) {
      item.qu++;
    },
    downQu: function(item) {
      item.qu--;
      if(item.qu <= 0) this.$emit('removeCartItem', item.id);
    },
  }
};
</script>

<style>
</style>
