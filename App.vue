<template>
  <div id="app">
    <h1>Playa del Carmen Weather</h1>
    <p><b>ID:</b>{{ result.id}}</p>
    <p><b>Name:</b>{{result.name}}</p>
    <p><b>Visibility:</b>{{result.visibility}}</p>
    <p><b>Id:</b>{{result.weather[0].id}}</p>
    <p><b>Main:</b>{{result.weather[0].main}}</p>
    <p><b>Description:</b>{{result.weather[0].description}}</p>
    <p><b>temperature:</b>{{result.main.temp}}</p>
    <router-view />
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "App",
  data() {
    return {
      APIkey: "018f46b23121f8a29e92c3e7be21b7cd",
      city: "Playa del Carmen",
    };
  },
  created() {
    this.getCurrentWeather();
  },
  methods: {
    getCurrentWeather() {
      axios
        .get(
          `https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=imperial&appid=${this.APIkey}`
        )
        .then((result) => {
          this.result = result.data;
          console.log(result.data);
        });
    },
  },
};
</script>
<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Quicksand", "sans-serif";
}
</style>
