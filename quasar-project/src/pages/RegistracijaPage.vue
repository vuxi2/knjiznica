<template>
  <q-page class="q-pa-md flex flex-center">
    <q-card class="q-pa-lg" style="width: 500px; max-width: 95vw;">
      <q-card-section>
        <div class="text-h6">Registracija korisnika</div>
      </q-card-section>

      <q-card-section class="q-gutter-md">
        <q-input filled v-model="ime" label="Ime" />
        <q-input filled v-model="prezime" label="Prezime" />
        <q-input filled v-model="email" label="Email" type="email" />
        <q-input filled v-model="korisnickoIme" label="Korisničko ime" />
        <q-input filled v-model="lozinka" label="Lozinka" type="password" />
      </q-card-section>

      <q-card-actions align="right">
        <q-btn color="primary" label="Potvrdi" @click="registriraj" />
      </q-card-actions>
    </q-card>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const ime = ref('')
const prezime = ref('')
const email = ref('')
const korisnickoIme = ref('')
const lozinka = ref('')

function registriraj() {
  if (!ime.value || !prezime.value || !email.value || !korisnickoIme.value || !lozinka.value) {
    alert('Molimo ispunite sva polja.')
    return
  }
  alert(`Registriran korisnik: ${ime.value} ${prezime.value}`)
}
</script>
