<script>
import Filter from '@/components/Filter.vue'
import Area from '@/components/Area/Area.vue'

export default {
  components: {
    Filter, Area
  },
  data() {
    return {
      basketlist: [],
      countryNum: "0",
      tours: [
        {Country:'Россия', town: 'Сочи', price: '200 000 руб'},
        {Country:'Россия', town: 'Сочи', price: '200 000 руб'},
        {Country:'Россия', town: 'Сочи', price: '200 000 руб'},
        {Country:'Россия', town: 'Сочи', price: '200 000 руб'},
        {Country:'Россия', town: 'Сочи', price: '200 000 руб'},
        {Country:'Франция', town: 'Париж', price: '300 000 руб'},
        {Country:'Франция', town: 'Париж', price: '300 000 руб'},
        {Country:'Франция', town: 'Париж', price: '300 000 руб'},
        {Country:'Франция', town: 'Париж', price: '300 000 руб'},
        {Country:'Франция', town: 'Париж', price: '300 000 руб'},
        {Country:'Франция', town: 'Париж', price: '300 000 руб'},
        {Country:'Тайланд', town: 'Бангкок', price: '100 000 руб'},
      ],
    }
  },
  methods: {
    basketElem(elem) {
      this.basketlist.push(elem)
    },
    countrycheck(data) {
      this.countryNum = data
    }
  }
}
</script>

<template>
  <div class="catalog">
    <div class="row">
      <Filter :tours="tours" @countrycheck="countrycheck"/>
      <Area @basketElem="basketElem" :tours="tours" :countryNum="countryNum" :basketlist="basketlist"/>
    </div>
  </div>
</template>

<style scoped>
.catalog {
  width: 100%;
  height: 100%;
  padding: 10px;
  margin-top: 70px;
}
</style>
