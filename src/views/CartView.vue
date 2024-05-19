<script setup>
import { useCartStore } from '../stores/cart'

import { storeToRefs } from 'pinia'

const store = useCartStore()
const { removeItems } = store

const { cartItems, sortedItems } = storeToRefs(store)

</script>

<template>
  <h1>This is the cart page</h1>

  <main v-if="sortedItems.length > 0">
    <div v-for="item in sortedItems" :key="item.id" class="item">
      <h1>{{ item.title }}</h1>
      <button @click="removeItems(item.id)">Remove</button>
    </div>
  </main>

  <main v-else>
    <h2>There is nothing in your cart</h2>
  </main>
</template>

<style>
  .item {
    width: 50em;
    height: auto;
    margin: 10px auto;
    border: solid black 3px;
  }

  button {
    margin-left: 10px;
    height: 20px;
    width: 70px;
  }
</style>