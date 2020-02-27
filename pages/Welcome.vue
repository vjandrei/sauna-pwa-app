<template>
  <div class="container text-left">
    <div>
      <h1 class="title">sauna-pwa-app</h1>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {}
  },
  mounted() {
    this.$OneSignal.push(() => {
      this.$OneSignal.isPushNotificationsEnabled((isEnabled) => {
        if (isEnabled) {
          console.log('Push notifications are enabled!')
        } else {
          console.log('Push notifications are not enabled yet.')
        }
      })
    })
    window.$OneSignal.push([
      'addListenerForNotificationOpened',
      (data) => {
        console.log('Received NotificationOpened:', data)
      }
    ])
  },
  beforeDestroy() {}
}
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
  @apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
</style>
