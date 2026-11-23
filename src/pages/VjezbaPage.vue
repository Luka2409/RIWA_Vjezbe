<template>
  <q-page padding>
  <div class="q-pa-md column items-start q-gutter-md">
    <q-card class="my-card">
      <q-card-section>
        {{ joke }}
      </q-card-section>
      <q-btn color="primary" label="Novi vic" @click="loadJoke" />
    </q-card>
    <q-card class="my-card">
      <q-card-section>
        {{ fact }}
      </q-card-section>
      <q-btn color="primary" label="Novi fact" @click="loadFact" />
    </q-card>
  </div>
  </q-page>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios';

const joke = ref('')

//let books = ref([])
onMounted(() => {
   loadJoke()
})
async function loadJoke() {
  await axios.get('https://dumbapis.com/joke')
    .then(result => {
    joke.value = result.data.joke
   })
   .catch(error => {
     console.error(error)
   })
}

const fact = ref('')

//let books = ref([])
onMounted(() => {
   loadFact()
})
async function loadFact() {
  await axios.get('https://catfact.ninja/fact')
    .then(result => {
    fact.value = result.data.fact
   })
   .catch(error => {
     console.error(error)
   })
}
</script>
