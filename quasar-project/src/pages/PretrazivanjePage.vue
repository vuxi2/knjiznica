<template>
  <q-page class="q-pa-md">
    <h2 class="q-mb-md">Pretraživanje knjiga</h2>

    <div class="q-gutter-md q-mb-md">
      <q-input
        filled
        v-model="pojam"
        label="Unesite pojam za pretraživanje"
        class="q-mb-sm"
      />

      <div class="row items-center q-gutter-sm">
        <q-checkbox v-model="pretraziPoNaslovu" label="Po naslovu" />
        <q-checkbox v-model="pretraziPoAutoru" label="Po autoru" />
      </div>

      <q-btn color="primary" label="Traži" @click="pretrazi" />
    </div>

    <q-table
      title="Rezultati pretraživanja"
      :rows="rezultati"
      :columns="columns"
      row-key="id"
      flat
      bordered
      v-if="rezultati.length > 0"
    />
    <div v-else class="text-grey q-mt-md">
      Nema rezultata pretraživanja.
    </div>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const pojam = ref('')
const pretraziPoNaslovu = ref(true)
const pretraziPoAutoru = ref(false)

const columns = [
  { name: 'id', label: 'ID', field: 'id', align: 'left' },
  { name: 'naslov', label: 'Naslov', field: 'naslov', align: 'left' },
  { name: 'autor', label: 'Autor', field: 'autor', align: 'left' },
  { name: 'status', label: 'Status', field: 'status', align: 'center' }
]

const knjige = ref([
  { id: 1, naslov: '12 pravila za život', autor: 'Jordan B. Peterson', status: 'slobodna' },
  { id: 2, naslov: 'Knjiga tisuću vrata', autor: 'Gareth Brown', status: 'zauzeta' },
  { id: 3, naslov: 'Umijeće ratovanja', autor: 'Sun Tzu', status: 'slobodna' },
  { id: 4, naslov: 'Šegrt Hlapić', autor: 'Ivana Brlić-Mažuranić', status: 'zauzeta' }
])

const rezultati = ref([])

function pretrazi() {
  const tekst = pojam.value.toLowerCase()
  rezultati.value = knjige.value.filter(knjiga => {
    if (pretraziPoNaslovu.value && knjiga.naslov.toLowerCase().includes(tekst)) return true
    if (pretraziPoAutoru.value && knjiga.autor.toLowerCase().includes(tekst)) return true
    return false
  })
}
</script>
