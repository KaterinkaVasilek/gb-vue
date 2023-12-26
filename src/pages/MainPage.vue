<script setup>
import "../assets/styles/index.scss";
import Icon from '@/components/Icon/Icon.vue';
import { ref } from "vue";

let items = ref([
  {
    title: "Яблоки",
    price: 1000
  },
  {
    title: "Морковь",
    price: 700
  },
  {
    title: "Ананас",
    price: 1200
  },
  {
    title: "Черри",
    price: 200
  },
  {
    title: "Апельсины",
    price: 800
  },
  {
    title: "Мандарины",
    price: 500
  },
  {
    title: "Гранат",
    price: 600
  },
  {
    title: "Арбуз",
    price: 1700
  }
]);

let productPrice = items.value;

const sortByPriceMin = () => {
  productPrice.sort((a, b) => a.price - b.price);
  items = productPrice;
}

const sortByPriceMax = () => {
  productPrice.sort((a, b) => b.price - a.price);
  items = productPrice;
}

</script>

<template>
  <div class="container">
    <div class="template">
      <div class="template__heading">
        <h2 class="template__title">Список товаров</h2>
        <div class="template__sort">
          <Icon class="template__icon" name="sort" />
          <div class="template__hidden">
            <button class="template__sort-btn" type="button" @click="sortByPriceMin">По цене (сначала дешевые)</button>
            <button class="template__sort-btn" type="button" @click="sortByPriceMax">По цене (сначала дорогие)</button>
          </div>
        </div>
      </div>
      <ul class="template__list">
        <li class="template__item" v-for="item in items" :key="item.title">
          <p>{{ item.title }}</p>
          <p>{{ item.price }}</p>
        </li>
      </ul>
    </div>
  </div>
</template>
