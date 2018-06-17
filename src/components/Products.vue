<template>
	<div class="products-list">
		<div 
		v-for="p in pList" 
		:key="p.id" 
		:class="{'selected': added(p.id) }" 
		class="product-item">
			<div class="name">{{p.name}}</div>
			<div class="price">{{p.price}}</div>
			<button @click="$emit('addProductToCart', p)" class="btn">Add</button>
		</div>
	</div>
</template>

<script>
export default {
  name: "Products",
  props: ["pList", "inCart"],
  methods: {
	  added: function(id){
		 return this.inCart.findIndex(function(_){return _ == id }) > -1
	  }
  }
};
</script>

<style lang="less">
.products-list {
	margin: 2em 0;
  .product-item {
    display: flex;
    justify-content: space-between;
	padding: 0.5em;
	  &.selected button {
		  background-color: #444;
		  color: #eee;
	  }
  }
  .product-item:nth-child(odd){
		background-color: #eee;
	}
}
</style>