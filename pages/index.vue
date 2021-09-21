<template>
  <div class="container">
    <div id="data">
      <h1>sauna-pwa-app</h1>
      <span class="block">Lämpötila: {{ saunaData.temp }} °C</span>
      <span class="block">Kosteus: {{ saunaData.humidity }} %</span>
      <svg class="progress-ring" height="220" width="220">
        <circle
          class="progress-ring__circle"
          stroke-width="10"
          stroke="#EBEDF8"
          fill="transparent"
          r="100"
          cx="110"
          cy="110"
        />
      </svg>
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
      saunaData: {}
    }
  },
  // vm = viewmodel
  created() {
    this.fireData.on('value', (snapshot) => {
      this.saunaData = snapshot.val()
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
  @apply border-gray-100 border w-1/2 p-12 flex flex-col justify-center items-center;
}

svg {
  @apply m-3;
}

.progress-ring__circle {
  --percent: 100;
  stroke-dashoffset: calc(220 - (var(--percent) * 220 / 100));
}
</style>
