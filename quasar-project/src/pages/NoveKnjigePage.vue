<template>
  <q-ajax-bar :hijack-filter="myFilterFn" />
</template>

<script>
export default {
  setup () {
    return {
      myFilterFn (url) {
        // example (only https://my-service.com/* should trigger)
        return /^https:\/\/my-service\.com/.test(url)
      }
    }
  }
}
</script>
