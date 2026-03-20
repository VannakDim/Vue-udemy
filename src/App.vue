<script>
import { reactive, ref, toRef, toRefs } from 'vue';

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
    // const nameRef = toRef(item,"name");
    // console.log('nameRef:', nameRef.value)
    // item.name = 'Angkor beer'
    // console.log('nameRef:', nameRef.value)

    const {name,price} = toRefs(item)
    // console.log('name:', itemRefs.name.value)
    // console.log('price:', itemRefs.price.value)
    // item.name = "Thai food"
    // item.price = 20
    return {
      message,
      qty,
      increment,
      decrement,
      name,
      price,
      swapProduct

    }
  }
};
</script>

<template>
  <h1>{{ name }}:{{ price }}</h1>
  <button @click="swapProduct">Swap</button>
  <h2>{{ qty }}</h2>
  <button @click="increment">+</button>
  <button @click="decrement">-</button>
  <input type="text" v-model="message"/>

</template>
