<script>
import CardItem from './CardItem.vue'

export default {
  components: {
    CardItem
  },
  props: {
    townName: {
      type: String
    },
    countryNum: {
      type: String
    },
    tours: {
      type: Array,
      required: true
    },
    basketlist:{
      type: Array
    }
  },
  data() {
    return {

    }
  },
  methods: {
    basketElem(qwe) {
      this.$emit('basketElem', qwe)
    }
  },
  computed: {
    filterCountry() {
      let q = []
      let eew = this.tours
      if (this.$route.path == '/Basket') {
        eew = this.basketlist
      }
      switch(this.countryNum) {
        case "1": q = eew.filter(function (elem) {if (elem.Country == 'Россия') return elem}); break;
        case "2": q = eew.filter(function (elem) {if (elem.Country == 'Франция') return elem}); break;
        case "3": q = eew.filter(function (elem) {if (elem.Country == 'Тайланд') return elem}); break;
        default: q = eew; break;
      }
      let t = this.townName;
      return q.filter(function (elem) {
        if(t==='') return true;
        return elem.town.indexOf(t) !== -1;
      })
    }
  }
}
</script>

<template>
  <CardItem 
    v-for="tour in filterCountry"
    :tour="tour"
    @basketElem="basketElem"
  />
</template>

<style>
.card-product {
  min-width: 200px;
}
</style>