<script setup>
import { useStore, useCart } from "../store/index.js";
import { ref } from "vue";
import Modal from '../components/Modal.vue';

const store = useStore();
await store.getMovies();

const movies = store.movies;
console.log(movies);


const showModal = ref(false);
const selectedId = ref(null);

const openModal = (value) => {
  showModal.value = true;
  selectedId.value = value;
};

const closeModal = () => {
  showModal.value = false;
};
</script>


<template>
  <div class="container">
    <div v-for=" (movie, index) in movies" class="movies">
      <p>
        {{ movie.title }}
      </p>
      <img v-if="movie.poster" :src="'https://image.tmdb.org/t/p/w500' + movie.poster" class="image"
        @click="openModal(movie)" />
      <Modal v-if="showModal" @toggleModal="closeModal()" :value="selectedId" />
    </div>
  </div>
</template>

<style scoped>
.movies {
  background-color: darkred;
  border-radius: 20px;
  padding: 10px;
  height: 100%;
  margin-bottom: 50px;
  color: white;
  font-family: 'Courier New', Courier, monospace;
  font-weight: bold;
  font-size: 120%;
  text-align: center;
}

.container {
  box-sizing: border-box;
  max-width: max-content;
  display: grid;
  margin-left: 2vw;
  margin-top: 1vw;
  gap: 2vw;
  column-gap: 2vw;
  grid-template-columns: auto auto auto;
}

.movies>img {
  height: 90.5%;
  width: 99%;
  margin: auto;
  border: 5px solid black;
}
</style>