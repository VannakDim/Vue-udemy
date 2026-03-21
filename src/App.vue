<script setup>
  import CartItem from './components/cartItem.vue';
  import useCart from './components/useCart';
  const {items, addItem, removeItem} = useCart()

    addItem(
      {
        id: 1,
        name: "Product X",
        price: 20,
        qty: 1
      }
    )
</script>


<template>
  <CartItem v-for="item in items" :cart-item="item" :key="item.id" @remove="removeItem" />
</template>
