<script setup>
import { computed, reactive, toRefs, onMounted, onUnmounted, onUpdated } from 'vue'

const props = defineProps({
    cartItem: {
            type: Object,
            required: true
        }
})

const emit = defineEmits(['remove'])


    const item = reactive(props.cartItem)

    const increment = () => item.qty++
    
    const decrement = () => item.qty--

    const total = computed(() => item.price * item.qty)

    const { name, price, qty } = toRefs(item)

    const remove = ()=> emit('remove', item)

    onMounted(()=>{
        console.log('Component mounted.')
    })

    onUpdated(()=>{
        console.log('Component updated.')
    })

    onUnmounted(()=>{
        console.log('Component unmounted.')
    })

</script>

<template>
  <h1>{{ name }} : {{ price }} : {{ qty }}</h1>

  <button @click="increment">+</button>
  <button @click="decrement">-</button>
  <br>
  <button @click="remove">Remove</button>

  <h3>Total: {{ total }}</h3>
</template>