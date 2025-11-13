<template>
  <q-page padding>
    <div>
      <q-input filled v-model="book.title" label="Naslov" />
      <q-input filled v-model="book.author" label="Autor" />
      <q-input filled v-model="book.description" label="Opis" type="textarea" />

      <q-file filled v-model="book.image" label="Odaberi sliku" accept="image/*" />

      <q-select
        filled
        v-model="book.status"
        :options="['Slobodna', 'Zauzeta']"
        label="Status"
      />

      <div class="q-mt-md">
        <q-btn label="Spremi" color="primary" @click="spremi" />
        <q-btn label="Odustani" color="secondary" @click="obrisi" />
      </div>
    </div>



    <div class="q-pa-md row items-start q-gutter-md">
      <q-card
        v-for="k in books"
        :key="k.id"
        class="my-card"
      >
        <img v-if="k.image" :src="getImageUrl(k.image)" />

        <q-card-section>
          <div class="text-h6">{{ k.title }}</div>
          <div class="text-subtitle2">{{ k.author }}</div>
        </q-card-section>

        <q-card-section class="q-pt-none">
          {{ k.description }}
        </q-card-section>

        <q-card-section>
  <q-chip
    :color="k.status === 'Slobodna' ? 'primary' : 'secondary'"
    text-color="white"
  >
    {{ k.status }}
  </q-chip>
</q-card-section>

      </q-card>
    </div>

    <div class="q-mt-lg">
      <h6>Spremljene knjige:</h6>
      <ul>
        <li v-for="k in books" :key="k.id">
          {{ k.id }}. {{ k.title }} – {{ k.author }} ({{ k.status }})
        </li>
      </ul>
    </div>
  </q-page>
</template>

<script setup>
import { ref } from 'vue';

const books = ref([]);
let nextId = ref(1);

const book = ref({
  title: '',
  author: '',
  description: '',
  image: null,
  status: 'Slobodna'
});

function spremi() {
  books.value.push({
    id: nextId.value,
    title: book.value.title,
    author: book.value.author,
    description: book.value.description,
    image: book.value.image,
    status: book.value.status
  });

  nextId.value++;
  obrisi();
}

function obrisi() {
  book.value = {
    title: '',
    author: '',
    description: '',
    image: null,
    status: 'Slobodna'
  };
}

function getImageUrl(file) {
  if (typeof file === 'string') return file;
  if (file instanceof File) return URL.createObjectURL(file);
  return '';
}
</script>

<style lang="sass" scoped>
.my-card
  width: 100%
  max-width: 250px
</style>


