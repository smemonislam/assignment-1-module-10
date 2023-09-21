<script setup>
import { ref, onBeforeMount } from 'vue'
import axios from 'axios'

const products = ref([])

onBeforeMount(async () => {
  await axios.get('https://dummyjson.com/products?limit=20&skip=20').then((res) => {
    products.value = res.data.products
  })
})

async function loadMore() {
  await axios.get('https://dummyjson.com/products?limit=20&skip=20').then((res) => {
    products.value = [...products.value, ...res.data.products]
  })
}
</script>
<template>
  <div class="row">
    <div class="col-lg-3 col-md-6" v-for="product in products" :key="product.id">
      <div class="card mb-3">
        <img :src="product.images[0]" class="card-img-top" alt="..." />
        <div class="card-body">
          <h5 class="card-title">{{ product.title }}</h5>
          <p class="card-text">price: {{ product.price }}.tk</p>
          <router-link :to="{ name: 'product', params: { id: product.id } }" class="btn btn-primary"
            >View Details</router-link
          >
        </div>
      </div>
    </div>
    <button @click="loadMore()" class="btn btn-primary mt-4 mb-5" v-if="products.length > 0">
      Load More
    </button>
  </div>
</template>
