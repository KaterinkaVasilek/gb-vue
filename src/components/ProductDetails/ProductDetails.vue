<script setup>
import './product-details.scss';
import { computed } from 'vue';

const product = [
  {
    id: 0,
    name: 'Name 1',
    price: 100,
    available: true
  },
  {
    id: 1,
    name: 'Name 2',
    price: 200,
    available: true
  },
  {
    id: 2,
    name: 'Name 3',
    price: 350,
    available: false
  },
  {
    id: 3,
    name: 'Name 4',
    price: 420,
    available: false
  },
  {
    id: 4,
    name: 'Name 5',
    price: 630,
    available: true
  }
]

const formattedPrice = (item) => {
  return `$ ${item}`;
}

</script>

<template>
  <div class="product-details">
    <ul class="product-details__list">
      <li class="product-details__item" v-for="item in product" :key="id">
        <p class="product-details__title">{{ item.name }}</p>
        <div class="product-details__desc">
          <p class="product-details__price">{{ formattedPrice(item.price) }}</p>
          <p class="product-details__info">{{ item.available ? 'Available' : 'Out of stock' }}</p>
        </div>
      </li>
    </ul>
  </div>
</template>