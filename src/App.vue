<template>
  <AverageTemperature msg="Welcome to Your Weather Reporter"/>
  <ForecastsView/>
</template>

<script>
import AverageTemperature from "@/components/AverageTemperature.vue";
import ForecastsView from "@/components/ForecastsView.vue";

export default {
  name: 'App',
  components: {
    AverageTemperature,
    ForecastsView
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #ffffff;
  margin-top: 60px;
}

body {
  background-color: #84a59d;
}

.feedback {
  background-color: #f4a261;
  border: none;
  border-radius: 4px;
  color: #ffffff;
  font-size: 16px;
  font-weight: bold;
  padding: 10px 20px;
  text-align: center;
  display: inline-block;
  transition: background-color 0.3s ease;
  cursor: pointer;
}

.feedback:hover {
  background-color: #f28482;
}
</style>
