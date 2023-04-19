<template>
  <div class="MoviewView">

    <h1>Activity with Quote</h1>

      <!-- React based display for API response !-->
      <b-list-group v-if="activityLoaded">
        <b-list-group-item>Activity: {{ activity }} </b-list-group-item>
        <b-list-group-item>Kanye says "{{ quote2 }}" </b-list-group-item>
      </b-list-group>

      <div v-else>
        <b-spinner label="Loading..."> Loading . . . </b-spinner>
      </div>

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
      activity: '',
      quote2: '',
      activityLoaded: false
    }},

    // individual methods that request from API's
    methods: {

      // request for Activity
      async getActivity () {

        const URL = "https://www.boredapi.com/api/activity"
        const res = await axios.get(URL)

        .catch((error) => { // error is handled in catch block
          if (error.response) { // status code out of the range of 2xx
            console.log("Data :" , error.response.data);
            console.log("Status :" + error.response.status);
          } else if (error.request) { // The request was made but no response was received
            console.log(error.request);
          } else {// Error on setting up the request
            console.log('Error', error.message);
          }
        })

        return new Promise(resolve => {

          setTimeout(() => {
            this.activity = res.data.activity;
            this.activityLoaded=true;
            resolve();
          }, 3000);
        })
      },

      // request for Quote
      async getQuote () {

        const URL = "https://api.kanye.rest/";
        const res = await axios.get(URL)

        .catch((error) => { // error is handled in catch block
          if (error.response) { // status code out of the range of 2xx
            console.log("Data :" , error.response.data);
            console.log("Status :" + error.response.status);
          } else if (error.request) { // The request was made but no response was received
            console.log(error.request);
          } else {// Error on setting up the request
            console.log('Error', error.message);
          }
        })
        
        this.quote2 = res.data.quote;

      }
    },
    // calling methods in the mounted hook
    async mounted() {
      await this.getActivity();
      this.getQuote();
    }
}


</script>