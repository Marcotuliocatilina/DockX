<template>
  <form @submit.prevent="handleSubmit">
    <div>
      <label for="user">User:</label>
      <input type="text" id="user" v-model="user" required />
    </div>
    <div>
      <label for="password">Password:</label>
      <input type="password" id="password" v-model="password" required />
    </div>
    <button type="submit">Login</button>
  </form>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const user = ref('')
const password = ref('')

function handleSubmit() {
  // Qui potresti aggiungere una chiamata API, validazione, ecc.
  alert(`User: ${user.value}\nPassword: ${password.value}`)
}
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  width: 300px;
  gap: 12px;
}

label {
  font-weight: bold;
}

input {
  padding: 6px;
  font-size: 1em;
}
</style>