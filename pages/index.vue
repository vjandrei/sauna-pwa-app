<template>
  <div class="container">
    <div id="data">
      <h1>
        sauna-pwa-app
      </h1>
    </div>
  </div>
</template>

<script>
export default {
  components: {},
  mounted() {},
  methods: {
    async readFromRealtimeDb() {
      const messageRef = this.$fireDb.ref('temp')
      try {
        const snapshot = await messageRef.once('value')
        alert(snapshot.val().message)
      } catch (e) {
        alert(e)
      }
    }
  }
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
