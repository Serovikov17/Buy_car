<script setup>
import { ref } from "vue";
import MyHeader from "./components/MyHeader/MyHeader.vue";
import CarBrands from "./components/CarBrands/CarBrands.vue";
import ListCars from "./components/ListCars/ListCars.vue";

const childMsg = ref("");
</script>

<template>
  <header class="header">
    <MyHeader />
  </header>
  <hr />
  <!-- Get data ( Brand, Model ) from CarBrands.vue -->
  <CarBrands @response="(msgData) => (childMsg = msgData)" />
  <hr />
  <!-- Transmit the received data from CarBrands.vue in ListCars.vue -->
  <ListCars :msgData="childMsg"> </ListCars>
</template>

<style lang="sass">
@import './assets/layouts/index'
</style>
