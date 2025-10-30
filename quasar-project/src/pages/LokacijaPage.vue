<template>
  <q-page class="q-pa-md">
    <h2 class="q-mb-md">Naša lokacija</h2>
    <div id="map" style="height:500px;"></div>
  </q-page>
</template>

<script>
import { ref, onMounted } from 'vue';
import * as L from 'leaflet';
import "leaflet/dist/leaflet.css";

export default {
  name: "LokacijaPage",
  setup(){
    const initialMap = ref('');
    onMounted(() => {
        initialMap.value = L.map('map').setView([45.3312,14.4322], 13);
        L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
            maxZoom: 19,
            attribution: '&copy;<a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
        }).addTo(initialMap.value);
         const marker = L.marker([45.3312,14.4322]).addTo(initialMap.value);
         marker.bindPopup('<b>Knjižnica</b><br>Rijeka, Hrvatska.').openPopup();
      })
      return {
        initialMap
      }
    }
}
</script>

<style scoped>
#map {
  height: 500px;
  width: 100%;
}
</style>
