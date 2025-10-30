<template>
  <q-page class="q-pa-md">
    <h2 class="q-mb-md">Popis svih knjiga</h2>

    <q-table
      title="Knjige"
      :rows="rows"
      :columns="columns"
      row-key="id"
      flat
      bordered
      :pagination="{ rowsPerPage: 5 }"
    >

      <template v-slot:body-cell-slika="props">
        <q-td :props="props">
          <q-img
            :src="props.row.slika"
            :alt="props.row.naslov"
            style="width: 50px; height: 70px; border-radius: 6px;"
            spinner-color="primary"
          />
        </q-td>
      </template>


      <template v-slot:body-cell-status="props">
        <q-td :props="props">
          <q-chip
            :color="props.row.status === 'slobodna' ? 'green' : 'red'"
            text-color="white"
            size="sm"
            class="text-capitalize"
          >
            {{ props.row.status }}
          </q-chip>
        </q-td>
      </template>
    </q-table>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const columns = [
  {
    name: 'id',
    label: 'ID',
    field: 'id',
    align: 'left',
    sortable: true,
    style: { fontSize: '14px' },
    headerStyle: { fontSize: '18px', fontWeight: 'bold' }
  },
  {
    name: 'naslov',
    label: 'Naslov',
    field: 'naslov',
    align: 'left',
    sortable: true,
    style: { fontSize: '14px' },
    headerStyle: { fontSize: '18px', fontWeight: 'bold' }
  },
  {
    name: 'autor',
    label: 'Autor',
    field: 'autor',
    align: 'left',
    sortable: true,
    style: { fontSize: '14px' },
    headerStyle: { fontSize: '18px', fontWeight: 'bold' }
  },
  {
    name: 'opis',
    label: 'Opis',
    field: 'opis',
    align: 'left',
    style: { fontSize: '14px' },
    headerStyle: { fontSize: '18px', fontWeight: 'bold' }
  },
  {
    name: 'slika',
    label: 'Slika',
    field: 'slika',
    align: 'center',
    style: { textAlign: 'center' },
    headerStyle: { textAlign: 'center', fontSize: '18px' }
  },
  {
    name: 'status',
    label: 'Status',
    field: 'status',
    align: 'center',
    sortable: true,
    style: { textAlign: 'center' },
    headerStyle: { textAlign: 'center', fontSize: '18px' }
  }
]

const rows = ref([
  {
    id: 1,
    naslov: '12 pravila za život',
    autor: 'Jordan B. Peterson',
    opis: 'Psihološko-filozofska knjiga s praktičnim pravilima za sretniji život.',
    slika: 'https://imgs.search.brave.com/yaSstenfWM5wdbx60dxu-QwLzQUquFYX7PXRm2M8Y0U/rs:fit:500:0:1:0/g:ce/aHR0cHM6Ly9jZG4x/LmxqZXZhay5oci8x/NTQ3MC1sYXJnZV9k/ZWZhdWx0LzEyLXBy/YXZpbGEtemEteml2/b3QuanBn',
    status: 'slobodna'
  },
  {
    id: 2,
    naslov: 'Knjiga tisuću vrata',
    autor: 'Gareth Brown',
    opis: 'Misteriozna i nadahnjujuća priča o knjizi koja povezuje različite svjetove.',
    slika: 'https://m.media-amazon.com/images/S/compressed.photo.goodreads.com/books/1685909433i/156480764.jpg',
    status: 'zauzeta'
  },
  {
    id: 3,
    naslov: 'Umijeće ratovanja',
    autor: 'Sun Tzu',
    opis: 'Klasično djelo o strategiji, taktici i mudrosti u životu i borbi.',
    slika: 'https://cdn11.bigcommerce.com/s-81ui0dgxz3/images/stencil/960w/products/11721/15975/1201889__36757.1739292116.jpg?c=1',
    status: 'slobodna'
  },
  {
    id: 4,
    naslov: 'Šegrt Hlapić',
    autor: 'Ivana Brlić-Mažuranić',
    opis: 'Poznata dječja priča o putovanju, dobroti i upornosti šegrta Hlapića.',
    slika: 'https://znanje.hr/product-images/c9c45bfd-ead4-419b-a939-b06ad8f21f35.jpg', 
    status: 'zauzeta'
  }
])
</script>
