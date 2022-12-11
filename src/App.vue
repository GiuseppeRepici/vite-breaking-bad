<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import axios from 'axios';
import { onMounted, ref } from 'vue'
import Character from './components/Character.vue';

const characters = ref([]);

const isLoading = ref(false);



onMounted(() => {
  getCharacters();
})


const getCharacters = async () => {
  try {
    isLoading.value = true;
    const res = await axios.get('https://rickandmortyapi.com/api/character');
    characters.value = res.data.results;
    isLoading.value = false;
  } catch (error) {
    console.log(error);
  }
}

</script>

<template>
  <div class="disclaimer">
    <p>Found {{ characters.length }} characters</p>
  </div>

  <div v-if="isLoading">
    <h1>LOADING...</h1>
  </div>

  <div class="container" v-if="!isLoading">
    <Character v-for="character in characters" :key="index" :data="character" />
  </div>
</template>

<style scoped>
.disclaimer {
  background-color: #333;
  text-align: left;
  padding: 8px;
  color: white;
  font-weight: bold;
}

.container {
  display: flex;
  flex-wrap: wrap;
  gap: 24px;
  justify-content: center;
  padding: 24px;
}
</style>
