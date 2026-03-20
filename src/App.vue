<script>
import CartItem from './components/cartItem.vue';
import { ref } from 'vue';

export default {
  components: { CartItem },
  setup(){
    const items = ref([
      {
        id: 1,
        name: "Product X",
        price: 20,
        qty: 1
      }
    ])

    const handleRemove = (date) => items.value.splice(0,1)
    return { items, handleRemove }
  }
}
</script>

<template>
  <CartItem v-for="item in items" :cart-item="item" :key="item.id" @remove="handleRemove" />
</template>
