<script>
import { computed, reactive, toRefs } from 'vue'

export default {
    props: {
        cartItem: {
            type: Object,
            required: true
        }
    },
  setup (props) {
    
    const item = reactive(props.cartItem)

    const increment = () => item.qty++
    
    const decrement = () => item.qty--

    const total = computed(() => item.price * item.qty)

    const { name, price, qty } = toRefs(item)

    return {
      qty,
      increment,
      decrement,
      name,
      price,
      total
    }
  }
}
</script>

<template>
  <h1>{{ name }} : {{ price }} : {{ qty }}</h1>

  <button @click="increment">+</button>
  <button @click="decrement">-</button>

  <h3>Total: {{ total }}</h3>
</template>