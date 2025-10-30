<template>
  <q-page class="q-pa-md flex flex-center">
    <q-card class="q-pa-lg" style="width: 400px; max-width: 90vw;">
      <q-card-section>
        <div class="text-h6">Prijava</div>
      </q-card-section>

      <q-card-section>
        <q-input filled v-model="username" label="Korisničko ime" />
        <q-input
          filled
          v-model="password"
          label="Lozinka"
          type="password"
          class="q-mt-md"
        />
      </q-card-section>

      <q-card-actions align="right">
        <q-btn color="primary" label="Potvrdi" @click="login" />
      </q-card-actions>
    </q-card>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const username = ref('')
const password = ref('')

function login() {
  if (!username.value || !password.value) {
    alert('Molimo unesite korisničko ime i lozinku.')
    return
  }
  alert(`Prijavljen korisnik: ${username.value}`)
}
</script>
