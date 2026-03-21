<script>
import CartItem from './components/cartItem.vue';
import useCart from './components/useCart';
import { ref } from 'vue';

export default {
  components: { CartItem },
  setup(){
    const {items, addItem, removeItem} = useCart()

    addItem(
      {
        id: 1,
        name: "Product X",
        price: 20,
        qty: 1
      }
    )

    
    return { items, removeItem }
  }
}
</script>

<template>
  <CartItem v-for="item in items" :cart-item="item" :key="item.id" @remove="removeItem" />
</template>
