<script>
export default {
  data() {
    return {
      Allcount: 0,
      Ruscount: 0,
      Francount: 0,
      Thcount: 0
    }
  },
  methods: {
    checkCountry(event) {
      this.$emit('countrycheck', event.target.value);
    }
  },
  props: {
    tours: {
      type: Array,
      required: true
    }
  },
  mounted() {
    this.Allcount = this.tours.length
    for (let i in this.tours) {

      switch (this.tours[i].Country) {
        case 'Россия':
          this.Ruscount += 1
          break
        case 'Франция':
          this.Francount += 1
          break
        default:
          this.Thcount += 1
          break
      }
    }
  }
}
</script>

<template>
    <div class="col-xl-3 col-lg-4 col-md-5">
        <div class="p-3">
          <div class="filter-sidebar-header">Страны</div>
          <div class="filter-sidebar-content">
            <div class="form-check">
              <input
                @input="checkCountry"
                class="form-check-input"
                type="radio"
                name="country"
                id="country-0"
                value="0"
                checked
              />
              <label class="form-check-label" for="country-0"> Все ({{ Allcount }}) </label>
            </div>
            <div class="form-check">
              <input
                @input="checkCountry"
                class="form-check-input"
                type="radio"
                name="country"
                id="country-1"
                value="1"
              />
              <label class="form-check-label" for="country-1"> Россия ({{ Ruscount }}) </label>
            </div>
            <div class="form-check">
              <input
                @input="checkCountry"
                class="form-check-input"
                type="radio"
                name="country"
                id="country-2"
                value="2"
              />
              <label class="form-check-label" for="country-2"> Франция ({{ Francount }}) </label>
            </div>
            <div class="form-check">
              <input
                @input="checkCountry"
                class="form-check-input"
                type="radio"
                name="country"
                id="country-3"
                value="3"
              />
              <label class="form-check-label" for="country-3"> Тайланд ({{ Thcount }}) </label>
            </div>
          </div>
        </div>
      </div>
</template>

<style>
.filter-sidebar-header {
  background: var(--primary);
  min-height: 40px;
  display: flex;
  align-items: center;
  color: var(--white);
  border-radius: 10px;
  font-size: 15px;
  padding: 0 5px;
}

.filter-sidebar-content {
  display: flex;
  flex-direction: column;
  gap: 10px;
  padding: 5px;
}
</style>