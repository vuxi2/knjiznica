<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn flat dense round icon="menu" aria-label="Menu" @click="toggleLeftDrawer" />

        <q-toolbar-title class="text-h2"> Novi naslov koji mi se više sviđa </q-toolbar-title>
  
        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <q-item-label header> Essential Links </q-item-label>

        <EssentialLink v-for="link in linksList" :key="link.title" v-bind="link" />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
  title: 'Početna',
  caption: 'Početna stranica',
  icon: 'favorite',
  link: '#/',
  },
    {
    title: 'Nove knjige',
    caption: 'popis novih knjiga',
    icon: 'book',
    link: '#/noveKnjige',
  },
  {
  title: 'Popis knjiga',
  caption: 'Popis svih knjiga',
  icon: 'menu',
  link: '#/popisKnjiga',
  },
  {
  title: 'Pretraživanje',
  caption: 'Pretraži',
  icon: 'search',
  link: '#/pretrazivanje',
  },
  {
  title: 'Lokacija',
  caption: '',
  icon: 'location_on',
  link: '#/lokacija',
  },
  {
  title: 'Login',
  caption: 'prijava',
  icon: 'login',
  link: '#/login',
  },
  {
  title: 'Registracija',
  caption: 'Registriraj se',
  icon: 'app_registration',
  link: '#/registracija',
  }

]

const leftDrawerOpen = ref(false)

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value
}
</script>
