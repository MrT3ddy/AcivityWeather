<template>
  <div class="MoviewView">
    <h1>Activity with Quote</h1>
      <!-- React based display for API response !-->
      <b-list-group>
        <b-list-group-item>Activity: {{ activity }} </b-list-group-item>
        <b-list-group-item>Kanye says "{{ quote2 }}" </b-list-group-item>
      </b-list-group>

       <!-- Link to vue router for Weather !-->
      Outdoor activity? Check the weather!
      <router-link to="/weather">Weather</router-link>
  </div>

</template>


<style scoped>
/* For title [h1] */
h1 {
  text-decoration: underline;
}
</style>
<script>


import axios from 'axios'
export default{
    
    data() {
      return{
        // holds variables for site
      activity: ' ',
      quote2: ''
    }},

    // individual methods that request from API's
    methods: {

      // request for Activity
      async getActivity () {
        const URL = "https://www.boredapi.com/api/activity"
        await axios.get(URL)
        .then ( res => {
          this.activity = res.data.activity;
        })
      },

      // request for Quote
      async getQuote () {
        const URL = "https://api.kanye.rest/"
        await axios.get(URL)
        .then ( res => {
          this.quote2 = res.data.quote;
        })
      }
    },
    // calling methods in the mounted hook
    mounted() {
      this.getActivity();
      this.getQuote();
    }
}


</script>