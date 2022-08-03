<template>
  <div class="container">
    <main v-if="!loading">
      <CovidData :text="title" :timestamp="timestamp" />
      <DataBoxes :stats="stats"></DataBoxes>
      <CountrySelect
        @get-country="getCountryData"
        :countries="countries"
      ></CountrySelect>

      <button
        v-if="stats.Country"
        @click="clearCountryData"
        class="bg-green-700 text-white rounded p-3 mt-10 focus:outline-none hover:bg-green-600"
      >
        Clear Country
      </button>
    </main>
    <main class="flex flex-col align-center justify-center text-center" v-else>
      <div class="text-gray-500 text-3xl mt-10 mb-6">
        Fetching the latest data for you ...
        <img :src="loadingImage" class="w-20 m-auto" alt="" srcset="" />
      </div>
    </main>
  </div>
</template>

<script>
import CovidData from "./CovidData.vue";
import DataBoxes from "./DataBoxes.vue";
import CountrySelect from "./CountrySelect.vue";

export default {
  name: "MainContainer",
  data() {
    return {
      loading: true,
      title: "Global",
      timestamp: "",
      stats: {},
      countries: [],
      loadingImage: require("../assets/loading.gif"),
    };
  },
  methods: {
    async fetchCovidData() {
      const response = await fetch("https://api.covid19api.com/summary");
      const apiResponse = await response.json();
      return apiResponse;
    },
    getCountryData(country) {
      this.stats = country;
      this.title = country.Country;
    },
    async clearCountryData() {
      this.loading = true;
      const data = await this.fetchCovidData();
      this.title = "Global";
      this.stats = data.Global;
      this.loading = false;
    },
  },
  async created() {
    console.log("Component is created successfully");
    const covidData = await this.fetchCovidData();

    this.stats = covidData.Global;
    console.log("this.stats");
    console.log(this.stats);
    // console.log(this.stats.NewConfirmed);
    this.countries = covidData.Countries;
    this.timestamp = covidData.Date;
    this.loading = false;

    // console.log(dataForIndia);
  },
  components: { CovidData, DataBoxes, CountrySelect },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
