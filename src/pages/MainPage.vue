<script setup>
import "../assets/styles/index.scss";
import Icon from '../components/Icon/Icon.vue'
import { reactive, ref } from "vue";

let reverseBtn = ref("Перевернуть");
const inputValue = ref('');
const items = reactive([
  {
    title: "Тайная комната"
  },
  {
    title: "Малавита"
  },
  {
    title: "Аферистка"
  }
]);
let item = {};

const reverse = () => {
  reverseBtn.value = reverseBtn.value.split("").reverse().join("");
};

const addMovie = () => {
  item.title = inputValue.value;
  items.push(item);
}

const removeMovie = () => {
  items.splice(item, 1);
}

</script>

<template>
  <div class="container template">
    <div class="intro">
      <p class="template__heading">Задание 1</p>
      <button class="intro__btn" @click="reverse">{{ reverseBtn }}</button>
    </div>
    <div class="movies">
      <p class="template__heading">Задание 2</p>
      <h2 class="movies__title">Список любимых фильмов</h2>
      <ul class="movies__list">
        <li class="movies__item" v-for="item in items" :key="item.title">
          <p>{{ item.title }}</p>
          <button class="movies__remove" @click="removeMovie">
            <Icon class="movies__icon" name="close" />
          </button>
        </li>
      </ul>
      <form class="movies__form" action="#">
        <label>
          <input class="movies__input" v-model="inputValue" type="text" name="movies__input" value=""
            placeholder="Введите название фильма">
        </label>
        <button class="movies__add" @click="addMovie">Добавить</button>
      </form>
    </div>
  </div>
</template>
