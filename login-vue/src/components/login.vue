<template>
  <div class="login-page">
    <div class="login-card" role="main" aria-labelledby="login-heading">
        <div class="logo-wrap" aria-hidden="true">
          <img :src="dxcLogo" alt="DXC logo" class="logo-img" />
        </div>
        <h2 id="login-heading">Sign in</h2>

      <form @submit.prevent="handleSubmit" novalidate>
        <div class="field">
          <label for="user">Username
            <span class="help" role="img" aria-hidden="false">
              <span class="help-icon" tabindex="0" aria-label="Username help" aria-describedby="user-help">?</span>
              <span class="help-tooltip" id="user-help" role="tooltip">Use your company username (e.g. firstname.lastname).</span>
            </span>
          </label>
          <input
            id="user"
            type="text"
            v-model="user"
            placeholder="Enter your username"
            :aria-invalid="!!errors.user"
            :aria-describedby="(errors.user ? 'user-error ' : '') + 'user-help'"
            autofocus
          />
          <p v-if="errors.user" id="user-error" class="error">{{ errors.user }}</p>
        </div>

        <div class="field">
          <label for="password">Password
            <span class="help" role="img" aria-hidden="false">
              <span class="help-icon" tabindex="0" aria-label="Password help" aria-describedby="password-help">i</span>
              <span class="help-tooltip" id="password-help" role="tooltip">Minimum 8 characters. Use a mix of letters and numbers.</span>
            </span>
          </label>
          <input
            id="password"
            type="password"
            v-model="password"
            placeholder="Enter your password"
            :aria-invalid="!!errors.password"
            :aria-describedby="(errors.password ? 'password-error ' : '') + 'password-help'"
          />
          <p v-if="errors.password" id="password-error" class="error">{{ errors.password }}</p>
        </div>

        <button class="btn" type="submit">Sign in</button>
      </form>
    </div>
  </div>
</template>

<script setup lang="ts">
const emit = defineEmits(['login'])
import { ref, reactive } from 'vue'
import dxcLogo from '../assets/dxc.svg'

const user = ref('')
const password = ref('')
const errors = reactive({ user: '', password: '' })

function validate() {
  errors.user = user.value.trim() ? '' : 'Please enter your username.'
  errors.password = password.value ? '' : 'Please enter your password.'
  return !errors.user && !errors.password
}

function handleSubmit() {
  if (!validate()) return
  // Qui potresti inviare le credenziali a un'API
  // emetti evento di login riuscito per mostrare la pagina successiva
  emit('login')
  // pulisci la password dopo l'invio (opzionale)
  password.value = ''
}
</script>

<style scoped>
.login-page {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(180deg,#f6f8fa,#eef2f6);
  padding: 2rem;
}
.login-card {
  width: 100%;
  max-width: 400px;
  background: #fff;
  border-radius: 12px;
  box-shadow: 0 6px 24px rgba(16,24,40,0.08);
  padding: 2rem;
  box-sizing: border-box;
}
h2 {
  margin: 0 0 1rem;
  font-size: 1.25rem;
  color: #111827;
}
.field {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  margin-bottom: 1rem;
}
label {
  font-weight: 600;
  font-size: 0.9rem;
  color: #374151;
}
input {
  padding: 0.6rem 0.75rem;
  border: 1px solid #e5e7eb;
  border-radius: 8px;
  font-size: 1rem;
  outline: none;
}
input:focus {
  border-color: #6366f1;
  box-shadow: 0 0 0 4px rgba(99,102,241,0.06);
}
.error {
  color: #b91c1c;
  font-size: 0.85rem;
  margin-top: 0.25rem;
}
.btn {
  width: 100%;
  padding: 0.75rem 1rem;
  border-radius: 8px;
  background: linear-gradient(90deg,#6366f1,#8b5cf6);
  color: white;
  font-weight: 600;
  border: none;
  cursor: pointer;
}
.btn:hover {
  opacity: 0.95;
  transform: translateY(-1px);
}
.logo-wrap {
  display: flex;
  justify-content: center;
  margin-bottom: 0.75rem;
}
.logo-img {
  width: 110px;
  height: auto;
  display: block;
}
.help {
  display: inline-block;
  margin-left: 0.5rem;
  position: relative;
}
.help-icon {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: #eef2ff;
  color: #3730a3;
  font-weight: 700;
  font-size: 0.75rem;
  line-height: 1;
  cursor: help;
}
.help-icon:focus {
  outline: 2px solid rgba(99,102,241,0.25);
}
.help-tooltip {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  bottom: calc(100% + 8px);
  background: #111827;
  color: white;
  padding: 0.5rem;
  border-radius: 6px;
  font-size: 0.85rem;
  white-space: nowrap;
  box-shadow: 0 6px 18px rgba(16,24,40,0.12);
  opacity: 0;
  pointer-events: none;
  transition: opacity 120ms ease-in-out, transform 120ms ease-in-out;
  transform-origin: bottom center;
}
.help:hover .help-tooltip,
.help-icon:focus + .help-tooltip,
.help-icon:focus-visible + .help-tooltip {
  opacity: 1;
  pointer-events: auto;
  transform: translateX(-50%) translateY(-4px);
}
@media (max-width: 420px) {
  .login-card { padding: 1.25rem; border-radius: 10px; }
}
</style>