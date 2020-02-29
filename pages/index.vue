<template>
  <div class="container">
    <div id="data">
      <h1>sauna-pwa-app</h1>
      <span class="block">Lämpötila: {{ saunaData.temp }} °C</span>
      <span class="block">Kosteus: {{ saunaData.humidity }} %</span>
    </div>
  </div>
</template>

<script>
import { DB } from '@/services/fireinit.js'
export default {
  components: {},
  asyncData({ store }) {
    return {
      fireData: DB.ref(`data`)
    }
  },
  data: () => {
    return {
      saunaData: {},
      items: {}
    }
  },
  created() {
    const vm = this
    this.fireData.on('value', function(snapshot) {
      vm.saunaData = snapshot.val()
    })
  },
  methods: {}
}
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
  @apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/

.container {
  @apply min-h-screen flex justify-center items-center text-center mx-auto;
}

#data {
  @apply border-gray-100 border w-1/2 p-12;
}
</style>
