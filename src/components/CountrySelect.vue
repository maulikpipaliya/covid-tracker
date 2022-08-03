<template>
  <div>
    <!-- {{ countries }} -->

    <select
      v-model="selected"
      @change="onChange()"
      class="form-select mt-1 block w-full border p-3 rounded mt-10"
    >
      <option value="0">Select Country</option>
      <option
        v-for="country in countries"
        :value="country.CountryCode"
        :key="country.ID"
      >
        {{ country.Country }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  name: "CountrySelect",
  props: ["countries"],
  data() {
    return {
      selected: 0,
    };
  },
  methods: {
    onChange() {
      const selectedCountry = this.countries.find(
        (country) => country.CountryCode == this.selected
      );
      console.log(selectedCountry);

      this.$emit("get-country", selectedCountry);
    },
  },
};
</script>
