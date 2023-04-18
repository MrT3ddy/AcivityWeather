<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      Find an activity and see what Kanye says. <br>
      If your up to it, check the weather! <br>
    </p>
    <h3>Options</h3>
    <ul>
      <li><router-link to="/activityquote">Activity</router-link></li>
      <li><router-link to="/weather">Temperature</router-link></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #3283A8;
}
</style>
