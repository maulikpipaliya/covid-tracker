<template>
  <div class="text-center">
    <h2 class="text-3xl font-bold">{{ text }}</h2>
    <div class="text-2xl mt-4 mb-10">
      {{ timestampFormatted }}
    </div>
  </div>
</template>

<script>
import moment from "moment";

export default {
  name: "CovidData",
  props: ["text", "timestamp"],
  computed: {
    timestampFormatted: function () {
      return moment(this.timestamp).format("MMMM Do YYYY, h:mm:ss a");
    },
  },
};
</script>

<style></style>
