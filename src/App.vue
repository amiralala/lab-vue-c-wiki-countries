
<script setup>
import Navbar from './components/Navbar.vue';
import CountriesList from './components/CountriesList.vue';




</script>

<template>
  <div class="app">
    <Navbar></Navbar>
    <router-view></router-view>
  </div>
</template>


<style>
.list-countries {
  display: flex;
  flex-direction: column;


}
</style>