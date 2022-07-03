<template>
  <h1 class="heading-container">1. TWOJE DANE</h1>

  <input type="checkbox" @click="isNewAccount = !isNewAccount" />
  <span>Nie masz konta? Zarejestruj się!</span>

  <form @submit.prevent v-if="isNewAccount" id="submit">
    <div>
      <input type="text" name="" id="" placeholder="Login" />
      <input type="password" name="" id="" placeholder="Hasło" />
      <input type="password" name="" id="" placeholder="Potwierdź hasło" />
      <input type="text" name="" id="" placeholder="Imię *" required />
      <input type="text" name="" id="" placeholder="Nazwisko *" required />
      <SelectView />
      <input type="text" name="" id="" placeholder="Adres *" required />
      <div class="">
        <input
          type="text"
          name=""
          id=""
          placeholder="Kod pocztowy *"
          class=""
          required
        />
        <input
          type="text"
          name=""
          id=""
          placeholder="Miasto *"
          class=""
          required
        />
      </div>

      <input type="text" name="" id="" placeholder="Telefon *" required />
      <button class="hide"></button>
    </div>
  </form>
</template>
<script setup>
import { ref } from 'vue'
import SelectView from './SelectView.vue'
const isNewAccount = ref(false)
const submitForm = () => document.getElementById('submit').submit()
</script>
