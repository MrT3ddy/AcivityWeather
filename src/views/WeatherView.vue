<template>
  
  <div class="MovieView">
    <u><h1>Search for Current Temperature</h1></u> <br>

        <!--  Search -->
    <div class="search-box">
      <label>Location </label>
      <input type="text" class="searchbox" placeholder = "Search" 
      v-model="searchvar"
      @keypress="sendRequest">
    </div>
      <!-- Displays direction if undefined-->
    <div class="undefined-wrap" v-if="weather.main == null">
          Input must be a location in text
    </div>
      <!-- Display API results if defined -->
    <div class="info-wrap" v-if="typeof weather.main != 'undefined'">
      <div class="Location"> {{ weather.name }}, {{weather.sys.country}} </div>
      <div class="Date">Today</div>
      <div class="temp">{{ weather.main.temp }}°</div>
    </div>
    
  </div>
  
  
  
  
</template>
<style scoped>
.undefined-wrap{
  color: #4a0905
}
</style>
<script>
export default {

  data() {
    return {
      // variables for api call
      url1: "http://api.weatherapi.com/v1/current.json?key=",
      api_key: "2cb8b08fd2bf972c9a19223b2ad94806",

      // varialbe for input binding
      searchvar: ' ',
      // object for result binding
      weather: {}
    };
  },

  methods: {

    // normal API request through method
    async sendRequest(e){
      if (e.key == "Enter"){

        fetch(`https://api.openweathermap.org/data/2.5/weather?q=${this.searchvar}&units=imperial&&appid=${this.api_key}`)
          .then(res => {
            return res.json();

          }).then(this.setResults);
          
      }
    },
    setResults (results) {
      this.weather = results
    }


  }}
</script>