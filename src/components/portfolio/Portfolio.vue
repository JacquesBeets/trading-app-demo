<template>
  <div>
    <div v-if="ifNoStock" class="alert alert-info" role="alert">Buy some stocks on the <router-link class="stockLink" to="/stocks">Stocks Page</router-link> to view them in your Portfolio.</div>
    <app-stock v-for="(stock, index) in stocks" :stock="stock" :key="index"></app-stock>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import Stock from './Stock.vue'

export default {
  computed: {
    ...mapGetters({
      stocks: 'stockPortfolio'
    }),
    ifNoStock() {
      return this.stocks == ''
    }
  },
  components: {
    'app-stock': Stock
  }
}
</script>

<style scoped>
.stockLink{
  text-decoration: underline;
}
</style>

