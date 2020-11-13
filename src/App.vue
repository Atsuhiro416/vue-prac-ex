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
      zipCode: "",
      allAddress: "",
      showAddress: "",
    }
  },


  methods: {
    async inputAddress() {
      let item = await axios.get(`https://apis.postcode-jp.com/api/v4/postcodes/${this.zipCode}?apikey=zabUzil9V6V3E2UG9HKDZ3WJfsx1QbRyyrc1sOC`);

      console.log(item);

      this.data = item.data;
      this.allAddress = this.data[0].allAddress;
      this.showAddress = this.allAddress;
    }
  }
}
</script>

<style>

</style>
