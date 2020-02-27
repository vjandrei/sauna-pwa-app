<template>
  <div class="container text-left">
    <div>
      <h1 class="title">
        sauna-pwa-app
      </h1>
    </div>
  </div>
</template>

<script>
 export default {
      data () {
        return {
            unwatchPushId: null
        }
      },
      mounted () {
        this.$OneSignal.push(() => console.log(this.$OneSignal))
      },
      beforeDestroy () {
        if (this.unwatchPushId) {
          this.unwatchPushId()
          this.unwatchPushId = null
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
</style>
