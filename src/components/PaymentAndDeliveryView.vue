<template>
  <h1 class="heading-container">2. METODA DOSTAWY</h1>

  <div v-for="{ text, key, id } in props.deliveryOption">
    <div class="delivers">
      <input type="radio" name="" v-model="supplier" :value="key" :key="id" />
      <span> {{ text }}</span>
    </div>
  </div>
  <!-- Show elements accordingly to checked radio inputs above -->

  <h1 class="heading-container">3. METODA PŁATNOŚCI</h1>
  <div v-if="supplier === ''">
    <div v-for="{ text, id, price, key } in props.payments">
      <div class="delivers">
        <input type="radio" :key="id" name="option" @click="addPrice(key)" />
        <span>
          {{ text }}
          {{ props.transformPrice(price) }} zł
        </span>
      </div>
    </div>
  </div>

  <div v-for="{ text, id, key, price } in props.payments">
    <div v-if="key === supplier">
      <div class="delivers">
        <input type="radio" :key="id" @click="addPrice(key)" />
        <span> {{ text }} {{ props.transformPrice(price) }} zł </span>
      </div>
    </div>
  </div>
  <h1 class="heading-container">4. PODSUMOWANIE</h1>
  <!-- calculate price -->
  <p>
    Testowy produkt:
    100
    zł
    <p>Ilość: 1</p>
  </p>
  <p class='add--border'>Suma częściowa 100 zł
     </p>
  <h3>Łącznie {{ deliveryPrice === 0 ? '100,00' : transformPrice(100 + deliveryPrice) }} zł </h3>
 
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
