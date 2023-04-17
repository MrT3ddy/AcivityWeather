<template>
  <div class="hello">
    <img alt="Vue logo" src="../assets/logo.jpeg">
    <HelloWorld msg="Activities and Weather "/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
// this page imports hello world vue for everything except the image, msg comes from this page
export default {
  name: 'HomeView',
  components: {
    HelloWorld
  }
}
</script>
