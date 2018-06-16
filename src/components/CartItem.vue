<template>
    <div>
      <span class="name">{{item.name}}</span>
      <div class="qu">
        <button @click="$emit('downQu',item)">-</button>
        <span>{{item.qu}}</span>
        <button @click="$emit('upQu',item)">+</button>
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
   
  }
};
</script>

<style>
</style>
