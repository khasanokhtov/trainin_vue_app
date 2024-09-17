<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'

import CardList from '../components/CardList.vue'

const favorites = ref([])

onMounted(async () => {
  try {
    const { data } = await axios.get(
      'https://16909ec46479d163.mokky.dev/favorites?_relations=items'
    )

    favorites.value = data.map((obj) => obj.item)
  } catch (e) {
    console.log(e)
  }
})
</script>

<template>
  <h1>Favorites</h1>
  <CardList :items="favorites" />
</template>
