<template>
  <h1 class="heading-container">2. METODA DOSTAWY</h1>

  <div v-for="{ text, key, id } in props.deliveryOption">
    <div>
      <input type="radio" name="" v-model="supplier" :value="key" :key="id" />
      <span> {{ text }}</span>
    </div>
  </div>
  <!-- Show elements accordingly to checked radio inputs above -->

  <h1 class="heading-container">3. METODA PŁATNOŚCI</h1>
  <div v-if="supplier === ''">
    <div v-for="{ text, id, price, key } in props.payments">
      <input type="radio" :key="id" name="option" @click="addPrice(key)" />
      <span>
        {{ text }}
        {{ props.transformPrice(price) }}
      </span>
    </div>
  </div>

  <div v-for="{ text, id, key, price } in props.payments">
    <div v-if="key === supplier">
      <input type="radio" :key="id" @click="addPrice(key)" />
      <span> {{ text }} {{ props.transformPrice(price) }} </span>
    </div>
  </div>
  <h1 class="heading-container">4. PODSUMOWANIE</h1>
  <p>
    cena:
    {{ deliveryPrice === 0 ? '100,00' : transformPrice(100 + deliveryPrice) }}
    zł
  </p>
</template>

<script setup>
import { ref } from 'vue'
const deliveryPrice = ref(0)

const addPrice = key => {
  deliveryPrice.value = prices.value[key]
  console.log(deliveryPrice.value)
  return deliveryPrice.value
}

const props = defineProps([
  'deliveryOption',
  'payments',
  'transformPrice',
  'supplier',
])

const prices = ref({
  dpd: 22,
  pick: 10.99,
  deliver: 18,
})
</script>
