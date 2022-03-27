<template>
  <div class="container-fluid" id="home-page">
    <div class="row">
      <div class="offset-md-3 col-12 col-md-6 text-center">
        <p>Covid data {{ data }}</p>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import axios from "axios";

export default defineComponent({
  async setup() {
    const data = await axios.get(
      "https://api.covidtracking.com/v1/states/current.json"
    );

    return { data };
  },
});
</script>
