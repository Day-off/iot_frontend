<template>
  <div>
    <h2>Forecasts</h2>
    <div class="col-sm-10 mx-auto">
      <table class="table">
        <caption>Forecasts Table</caption>
        <thead>
        <tr>
          <th>Date</th>
          <th>Night</th>
          <th>Day</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="forecast in forecasts.forecastList" :key="forecast.date">
          <td>{{ forecast.date }}</td>
          <td>
            <ul>
              <li><strong>Weather:</strong> {{ forecast.night.phenomenon }}</li>
              <li><strong>Min temperature:</strong> {{ forecast.night.tempmin }}</li>
              <li><strong>Max temperature:</strong> {{ forecast.night.tempmax }}</li>
              <li><strong>More info:</strong> {{ forecast.night.text }}</li>
            </ul>
          </td>
          <td>
            <ul>
              <li><strong>Weather:</strong> {{ forecast.day.phenomenon }}</li>
              <li><strong>Min temperature:</strong> {{ forecast.day.tempmin }}</li>
              <li><strong>Max temperature:</strong> {{ forecast.day.tempmax }}</li>
              <li><strong>More info:</strong> {{ forecast.day.text }}</li>
            </ul>
          </td>
        </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      forecasts: {
        forecastList: []
      }
    }
  }
  ,
  created() {
    axios.get('/api/getFullReport').then(response => {
      this.forecasts.forecastList = response.data.forecastList;
    })
  }
}
</script>
<style>.table {
  border-collapse: separate;
  border-spacing: 0;
  width: 100%;
  max-width: 100%;
  margin-bottom: 1rem;
  background-color: #f28482;
  border-radius: 1rem;
  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.1);
}

tr:nth-child(n):hover{
  background-color: #f4a261;
  opacity: 100;
}

th, td {
  text-align: center;
  vertical-align: middle;
  padding: 0.75rem;
  border-bottom: 1px solid #dee2e6;
}

tbody tr:nth-child(even){
  transition: background-color 0.3s ease;
}

th {
  font-weight: bold;
  background-color: #f28482;
  color: #ffffff;
  border-radius: 0.5rem 0.5rem 0 0;
  transition: background-color 0.3s ease;
}


tbody tr:nth-child(odd) {
  border: #f4a261;
  background-color: #f38f8d;
  border-bottom-width: medium;
  transition: background-color 0.3s ease;
}

tbody tr:last-child td:first-child {
  border-bottom-left-radius: 1rem;
}

tbody tr:last-child td:last-child {
  border-bottom-right-radius: 1rem;
}


</style>