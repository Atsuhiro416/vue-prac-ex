<template>
  <div id="app">
    <input type="text" v-model="zipCode">
    <button @click="inputAddress">住所自動入力</button>
    <p>Address：{{ showAddress }}</p>
    <router-view/>
  </div>
</template>
 <script>
import axios from "axios";

export default {
  data() {
    return {
      zipCode: 1140002,
      allAddress: "",
      showAddress: "",
      api: "",
      apikey: ""
    }
  },

  // async created() {
  //   let item = await axios.get(
  //     'https://apis.postcode-jp.com/api/v4/postcodes/' + 1140002 + '?apikey=zabUzil9V6V3E2UG9HKDZ3WJfsx1QbRyyrc1sOC',

  //   );

  //   console.log(item);

  //   this.data = item.data
  //   this.allAddress = this.data.allAddress;
  // },

    async mounted() {
     let item = await axios.get(`https://apis.postcode-jp.com/api/v4/postcodes/${this.zipCode}?apikey=zabUzil9V6V3E2UG9HKDZ3WJfsx1QbRyyrc1sOC`);

    console.log(item);

    this.data = item.data;
    this.allAddress = this.data.allAddress;
  },

  methods: {
    inputAddress() {
      this.showAddress = this.allAddress;
    }
  }
}
</script>

<style>

</style>
