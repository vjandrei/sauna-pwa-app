<template>
  <div class="container">
    <div id="data">
      <h1>sauna-pwa-app</h1>
      <span class="block">Lämpötila: -- °C</span>
      <span class="block">Kosteus: -- %</span>
    </div>
    {{ todos }}
    <li v-for="todo in todos" :key="todo.id">
      {{ todo.id }}
    </li>
  </div>
</template>

<script>
import firebase from 'firebase/app'
import 'firebase/database'

const config = {
  apiKey: process.env.FIREBASE_APP_KEY,
  authDomain: process.env.FIREBASE_AUTH_DOMAIN,
  databaseURL: process.env.FIREBASE_DATABASE_URL,
  storageBucket: process.env.FIREBASE_STORAGE_BUCKET,
  messagingSenderId: process.env.FIREBASE_MESSAGING_SENDER_ID,
  projectId: process.env.FIREBASE_PROJECT_ID
}

export const db = firebase.initializeApp(config).database()

export default {
  components: {},
  data: () => {
    return {
      saunaData: [],
      todos: []
    }
  },
  props: {
    database: {}
  },
  firebase: {
    database: db.ref('todos').push()
  },
  mounted() {},
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
