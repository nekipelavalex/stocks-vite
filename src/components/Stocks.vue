<template>
  <div class="stock">
    <div class="stock-item" v-for="value in stock" :key="value.stock">
      <div class="stock-item__info">
        <div class="stock-item__cover">
          <img :src="value.image" :alt="value.companyName" />
        </div>
        <h3 class="stock-item__title">
          {{ value.companyName }}
          <span>{{ value.symbol }}</span>
        </h3>
      </div>
      <span class="stock-item__price">{{ value.price }} $</span>
    </div>
  </div>
  <h3>Get Info</h3>
  <select v-model="selected">
    <option value="" disabled>Select Company</option>
    <option v-for="value in stock" :key="value.stock" :value="value.description">
      {{ value.companyName }}
    </option>
  </select>
  <div class="info">{{ selected }}</div>
</template>

<script lang="ts">
import exios from "axios"
export default {
  name: "Stocks",
  data() {
    return {
      stock: [],
      errors: [],
      selected: ''
    }
  },
  created() {
    exios.get('https://financialmodelingprep.com/api/v3/profile/AAPL,NVDA,TSLA,AMD,INTC,MDB,AMZN,PINS,DAL,OKTA,TRIP,GDDY?apikey=5a8358cbf4b1aa3d063740f2a1f22b19')
      .then(responce => {
       this.stock = responce.data
       console.log(responce)
     })
     .catch(e => {
       this.errors.push(e)
     })
   }
}
</script>
