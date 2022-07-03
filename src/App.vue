<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <UserDataView />

  <PaymentAndDeliveryView
    :deliveryOption="deliveryOption"
    :payments="payments"
    :transformPrice="transformPrice"
    :supplier="supplier"
  />
</template>

<script setup>
import UserDataView from './components/UserDataView.vue'
import PaymentAndDeliveryView from './components/PaymentAndDeliveryView.vue'

import { ref } from 'vue'
const supplier = ref('')
// const props = defineProps(['deliveryOption', 'payments'])

const transformPrice = price =>
  price.toString().length < 4
    ? `${price},00`
    : price.toString().split('.').join(',')

let id = 0

const deliveryOption = ref([
  { text: 'Paczkomaty 24/7', id: id++, key: 'pick' },
  { text: 'Kurier DPD', id: id++, key: 'deliver' },
  { text: 'Kurier DPD pobranie', id: id++, key: 'dpd' },
])

const payments = ref([
  {
    text: 'PayU',
    id: id++,
    key: 'pick',
    price: 10.99,
  },
  {
    text: 'Płatność przy odbiorze',
    id: id++,
    key: 'deliver',
    price: 18.0,
  },
  {
    text: 'Przelew bankowy - zwykły',
    id: id++,
    key: 'dpd',
    price: 22.0,
  },
])
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
