<template>
  <div>
    <div class="grid md:grid-cols-2 gap-4">
      <!-- Box1 -->
      <div class="shadow-md bg-blue-100 p-10 text-center rounded">
        <h3 class="text-3xl text-blue-900 font-bold mb-4">Cases</h3>
        <div class="text-2xl mb-4">
          <span class="font-bold"> New: </span>
          {{ numberWithCommas(stats.NewConfirmed) }}
        </div>
        <div class="text-2xl mb-4">
          <span class="font-bold"> Total: </span>
          {{ numberWithCommas(stats.TotalConfirmed) }}
        </div>
      </div>

      <!-- Box2 -->
      <div class="shadow-md bg-red-300 p-10 text-center rounded">
        <h3 class="text-3xl text-blue-900 font-bold mb-4">Deaths</h3>
        <div class="text-2xl mb-4">
          <span class="font-bold"> New: </span>
          {{ numberWithCommas(stats.NewDeaths) }}
        </div>
        <div class="text-2xl mb-4">
          <span class="font-bold"> Total: </span>
          {{ numberWithCommas(stats.TotalDeaths) }}
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "DataBoxes",
  props: ["stats"],
  methods: {
    numberWithCommas(num) {
      return num.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    },
  },
  mounted() {
    console.log("mounted- this.stats");
    console.log(this);
  },
};
</script>
<style lang=""></style>
