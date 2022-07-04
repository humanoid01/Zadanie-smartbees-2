<template>
  <h1 class="heading-container">1. TWOJE DANE</h1>

  <input type="checkbox" @click="isNewAccount = !isNewAccount" />
  <span>Nie masz konta? Zarejestruj się!</span>
  <!-- register form -->
  <form @submit.prevent v-if="isNewAccount" id="submit" class="register">
    <div>
      <input type="text" name="" :id="id++" placeholder="Login" />
      <input type="password" name="" :id="id++" placeholder="Hasło" />
      <input type="password" name="" :id="id++" placeholder="Potwierdź hasło" />
      <input type="text" name="" :id="id++" placeholder="Imię *" required />
      <input type="text" name="" :id="id++" placeholder="Nazwisko *" required />
      <SelectView />
      <input type="text" name="" :id="id++" placeholder="Adres *" required />
      <div class="">
        <input
          type="text"
          name=""
          :id="id++"
          placeholder="Kod pocztowy *"
          class=""
          required
        />
        <input
          type="text"
          name=""
          :id="id++"
          placeholder="Miasto *"
          class=""
          required
        />
      </div>

      <input type="text" name="" :id="id++" placeholder="Telefon *" required />
      <button class="hide"></button>
    </div>
  </form>
</template>
<script setup>
import { ref } from 'vue'
import SelectView from './SelectView.vue'
const isNewAccount = ref(false)
let id = 1000
</script>
