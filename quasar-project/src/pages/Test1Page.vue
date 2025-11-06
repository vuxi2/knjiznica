<template>
  <q-page padding>
      <div class="q-pa-md q-gutter-sm">
    <q-btn push color="white" text-color="primary" label="Unread Mails">
      <q-badge color="orange" floating>{{Unread}}</q-badge>
    </q-btn>

    <q-btn dense color="purple" round icon="email" class="q-ml-md">
      <q-badge color="red" floating>{{open}}</q-badge>
    </q-btn>
  </div>
  
  
    <div class="q-pa-md row items-start q-gutter-md">
    <q-card class="my-card bg-secondary text-white">
      <q-card-section>
        <div class="text-h6">{{msg[0].title}}</div>
        <div class="text-subtitle2">{{msg[0].autor}}</div>
      </q-card-section>

      <q-card-section>
        {{ msg[0].tekst }}
      </q-card-section>
            <q-separator dark />

      <q-card-actions>
        <q-btn flat @click="openMsg">open</q-btn>
        <q-btn flat @click="deleteMsg">delete</q-btn>
      </q-card-actions>
    </q-card>
    </div>
  </q-page>
</template>

<script setup>
import { ref } from "vue"
  const msg=[
    {
    title:"Changing Planet",
    autor:"John Doe",
    tekst:"Lorem ipsum"
    }
]
//const title="Changing Planet"
//const autor="John Doe"
//const tekst="Lorem ipsum"
let Unread = ref(22)
let open = ref(4)

function openMsg() {
  open.value -= 1
  console.log("open"+open.value)
}
function deleteMsg() {
  Unread.value -= 1
  console.log("delete"+Unread.value)
}
</script>


<style lang="sass" scoped>
.my-card
  width:100%
  max-width: 250px
</style>