<template>
  <select
    @change="onChange"
    v-model="selected"
    class="form-select mt-5 block w-full border p-3 rounded"
  >
    <option value="0">Select Country</option>
    <option v-for="country in countries" :key="country.ID" :value="country.ID">
      {{ country.Country }}
    </option>
  </select>
</template>

<script>
export default {
  name: "CountrySelect",
  props: {
    countries: {
      type: Array
    }
  },
  data() {
    return {
      selected: 0
    };
  },
  methods: {
    onChange() {
      const countryData = this.countries.find(
        item => item.ID === this.selected
      );
      this.$emit("get-country", countryData);
    }
  }
};
</script>