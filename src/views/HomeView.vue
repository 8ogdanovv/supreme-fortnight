<template>
  <div>
    <h1>Home</h1>
    <ul>
      <li v-for="{
        id,
        title,
        description,
        price,
        discountPercentage,
        rating,
        stock,
        brandGolden,
        category,
        thumbnail,
        images
      }, index in products" :key="index">
        {{ id }}
        {{ title }}
        {{ description }}
        {{ price }}
        {{ discountPercentage }}
        {{ rating }}
        {{ stock }}
        {{ brandGolden }}
        {{ category }}
        <img :src="thumbnail" :alt="index" width="5%">
        {{ images }}
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref, onBeforeMount } from 'vue'

const products = ref([])

const apiURL = 'https://dummyjson.com/products'

async function fetchProducts() {
  try {
    const response = await fetch(apiURL)
    const data = await response.json()
    return data.products
  } catch (error) {
    console.error('Error fetching products:', error)
    return []
  }
}

onBeforeMount(async () => {
  products.value = await fetchProducts()
})
</script>

<!-- {
  "id": 30,
  "title": "Key Holder",
  "description": "Attractive DesignMetallic materialFour key hooksReliable & DurablePremium Quality",
  "price": 30,
  "discountPercentage": 2.92,
  "rating": 4.92,
  "stock": 54,
  "brand": "Golden",
  "category": "home-decoration",
  "thumbnail": "https://cdn.dummyjson.com/product-images/30/thumbnail.jpg",
  "images": [
      "https://cdn.dummyjson.com/product-images/30/1.jpg",
      "https://cdn.dummyjson.com/product-images/30/2.jpg",
      "https://cdn.dummyjson.com/product-images/30/3.jpg",
      "https://cdn.dummyjson.com/product-images/30/thumbnail.jpg"
  ]
} -->
