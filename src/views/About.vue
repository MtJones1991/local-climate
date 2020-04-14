<template>
  <div class="home">
    <main>
      <div class="search-box">
        <input
          type="text"
          class="search-bar"
          placeholder="search-bar"
          v-model="query"
          @keypress="fetchWeather"
        />
      </div>

      <div class="weather-wrap" v-if="typeof this.$store.state.weather.main != 'undefined'">
        <div class="location-box">
          <div class="location">
            {{ this.$store.state.weather.name }},
            {{ this.$store.state.weather.sys.country }}
          </div>
          <div class="date">{{ this.todaysDate }}</div>
        </div>
      </div>

      <div class="location-box" v-else>
        <div class="instructions">Enter a location</div>
        <div class="date">{{ this.todaysDate }}</div>
      </div>

      <div class="weather-box" v-if="typeof this.$store.state.weather.main != 'undefined'">
        <div class="temp">{{ Math.round(this.$store.state.weather.main.temp) }}°c</div>
        <div class="weather">{{ this.formattedWeather }}</div>
      </div>
    </main>
  </div>
</template>

<script>
import axios from "axios";
import moment from "moment";
import router from "../router.js";
const API_KEY = process.env.VUE_APP_API_KEY;
// @ is an alias to /src

export default {
  name: "about",
  components: {},
  data() {
    return {
      url_base: "https://api.openweathermap.org/data/2.5/",
      query: "",
      weather: {}
    };
  },

  methods: {
    fetchWeather(e) {
      if (e.key == "Enter") {
        axios
          .get(
            `${this.url_base}weather?q=${this.query}&units=metric&APPID=${API_KEY}`
          )

          // fetch()
          // `${this.url_base}weather?q=${this.query}&units=metric&APPID=${API_KEY}`
          .then(res => {
            console.log(res.data);
            this.$store.commit("setWeather", res.data);
          });
      }
    }
  },

  computed: {
    todaysDate() {
      let date = new Date();
      return moment(date).format("dddd, Do MMMM YYYY");
    },

    formattedWeather() {
      return this.$store.state.weather.weather[0].description
        ? this.$store.state.weather.weather[0].description
            .charAt(0)
            .toUpperCase() +
            this.$store.state.weather.weather[0].description.slice(1)
        : "";
    }
  }
};
</script>

<style scoped>
.search-box {
  width: 100%;
  margin-bottom: 30px;
}

.search-box .search-bar {
  display: block;
  width: 100%;
  padding: 10px;

  color: #313131;
  font-size: 21px;

  appearance: none;
  border: none;
  outline: none;
  background: none;

  box-shadow: 0px 0px 7px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.6);
  border-radius: 0px 15px 0px 15px;
  transition: 0.5s;
}

.search-box .search-bar:focus {
  background-color: rgba(255, 255, 255, 0.9);
}

.location-box .location {
  color: #fff;
  font-size: 31px;
  font-weight: 495;
  text-align: center;
  text-shadow: 1px 3px rgba(255, 255, 255, 0.25);
}

.location-box .date,
.instructions {
  color: #fff;
  font-size: 21px;
  font-weight: 305;
  font-style: italic;
  text-align: center;
  text-shadow: 1px 3px rgba(255, 255, 255, 0.25);
}

.weather-box {
  text-align: center;
}

.weather-box .temp {
  display: inline-block;
  padding: 10px 25px;
  color: #fff;
  font-size: 95px;
  font-weight: 895;

  text-shadow: 3px 5px rgba(255, 255, 255, 0.25);
  background-color: rgba(255, 255, 255, 0.25);

  border-radius: 15px;
  margin: 25px 0px;

  box-shadow: 3px 5px rgba(0, 0, 0, 0.25);
}

.weather-box .weather {
  color: #fff;
  font-size: 47px;
  font-weight: 695;
  font-style: italic;
  text-shadow: 3px 5px rgba(0, 0, 0, 0.25);
}
</style>
