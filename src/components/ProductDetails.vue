<script setup>
import { reactive, onBeforeMount } from 'vue'
import axios from 'axios'
import { useRoute } from 'vue-router'

const product = reactive({})
const route = useRoute()
const id = route.params.id

onBeforeMount(async () => {
  await axios.get(`https://dummyjson.com/products/${id}`).then((res) => {
    product.id = res.data.id
    product.title = res.data.title
    product.description = res.data.description
    product.images = res.data.images[0]
    product.price = res.data.price
  })
})
</script>
<template>
  <div class="row">
    <div class="col-md-4">
      <img :src="product.images" :alt="product.title" class="img-fluid" />
    </div>
    <div class="col-md-8">
      <h2>{{ product.title }}</h2>
      <p>{{ product.description }}</p>
      <span>Price: {{ product.price }}.tk</span>
    </div>
  </div>
</template>
