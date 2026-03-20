<script>
import { computed, reactive, ref, toRef, toRefs, watch, watchEffect } from 'vue';

export default {
  
  setup(){
    const message = ref("Hello")
    const item = reactive({
      name : "Khmer Food",
      price : 12,
      qty: 1
    })
    const decrement =()=> item.qty--
    const increment =()=> item.qty++
    const swapProduct = ()=>{
      item.name = "Product A"
      item.price = 30
    }
    const total = computed(() => item.price * item.qty)
    const { name, price, qty } = toRefs(item)

    watch(()=> item.qty, ()=>{
      if(item.qty === 5)
      alert("You cannot add more item")
    }, { immediate: true })

    watchEffect(()=>{
      console.log('Price change: ',item.price )
    })
    return {
      qty,
      message, 
      increment,
      decrement,
      name,
      price,
      total,
      swapProduct

    }
  }
};
</script>

<template>
  <h1>{{ name }} : {{ price }}</h1>
  <button @click="swapProduct">Swap product</button>
  <button @click="price++">Increment price</button>

  <h2>{{ qty }}</h2>
  <button @click="increment">+</button>
  <button @click="decrement">-</button>

  <h3>Total: {{ total }}</h3>
</template>
