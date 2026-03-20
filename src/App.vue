<script>
import { reactive, ref } from 'vue';

export default {
  setup(){
    const message = ref("Hello")
    const qty = ref(1)
    const item = reactive({
      name : "Khmer Food",
      price : 12
    })
    const increment = qty.value++
    const decrement = qty.value--
    const swapProduct = ()=>{
      item.name = "Product A"
      item.price = 30
    }
    return {
      message,
      qty,
      increment,
      decrement,
      item,
      swapProduct

    }
  }
};
</script>

<template>
  <h1>{{ item.name }}:{{ item.price }}</h1>
  <button @click="swapProduct">Swap</button>
  <h2>{{ qty }}</h2>
  <button @click="increment">+</button>
  <button @click="decrement">-</button>
  <input type="text" v-model="message"/>

</template>
