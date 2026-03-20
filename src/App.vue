<script>
import { ref } from 'vue';

export default {
  setup(){
    const message = ref("Hello")
    const qty = ref(1)
    const increment = ()=> qty.value++
    const decrement = ()=>qty.value--
    return {
      message,
      qty,
      increment,
      decrement

    }
  }
};
</script>

<template>
  <h1>{{ message }}</h1>
  <h2>{{ qty }}</h2>
  <button @click="increment">+</button>
  <button @click="decrement">-</button>
  <input type="text" v-model="message"/>

</template>
