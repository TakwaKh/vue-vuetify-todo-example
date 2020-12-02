<template>
  <v-app>
    <Navbar/>
    <v-main>
      <router-view class="px-5 pt-4"></router-view>
    </v-main>
  </v-app>
</template>

<script>
import Navbar from './components/Navbar';

export default {
  name: 'App',

  components: {
    Navbar,
  },

  data: () => ({
    //
  }),
};
</script>
<style >
@import url("https://cdn.jsdelivr.net/npm/@mdi/font@5.x/css/materialdesignicons.min.css"); 
.v-main{
  background-color: #F4F7F8;
}
</style>
