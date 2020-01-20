<template>
  <v-layout fill-height>
    <NooNoo/>
  </v-layout>
</template>

<script>
// @ is an alias to /src
import NooNoo from '@/components/NooNoo.vue'

export default {
  name: 'home',
  components: {
    NooNoo
  }
}
</script>
