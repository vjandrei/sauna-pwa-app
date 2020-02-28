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
export default {
  components: {},
  data: () => {
    return {
      saunaData: []
    }
  },
  mounted() {
    fetch('https://mokki-sauna.firebaseio.com/data.json').then((response) => {
      response.json().then((saunaData) => {
        this.saunaData = saunaData
      })
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
