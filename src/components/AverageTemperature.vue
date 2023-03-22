<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div>
      <br>
      <h3><strong>Average Temperature in Estonia: </strong></h3>
      <p>{{ this.temperature }}</p>
      <div class="col-sm-6 mx-auto" style="padding: 1px">
        <input type="submit" v-on:click="getAverageTemperature" class="feedback" value="Update info ^">
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      temperature: "",
    }
  },
  props: {
    msg: String
  },
  created() {
    axios.get('/api/getAverageTemperature').then(response => {
      this.temperature = response.data;
    })
  },
  methods: {
    getAverageTemperature() {
      axios.get('/api/getAverageTemperature')
          .then(response => {
            this.temperature = response.data
            console.log(response.data)
          })
          .catch(error => {
            console.error(error)
          })
    }
  }
}
</script>
<style>
p {
  font-size: 1.2rem;
  color: #ffffff;
  background-color: #f28482;
  border: 1px solid #ddd;
  padding: 1rem;
  border-radius: 0.5rem;
  display: inline-block;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

</style>
