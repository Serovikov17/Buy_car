<script setup>
import { ref, onMounted } from "vue";
import ListCarsOverlay from "./ListCarsOverlay.vue";
import localDataCars from "../../myCars.json";
/* import axios from "axios"; */

//Request to get data from the database
/* const carsData = ref([]);
onMounted(async () => {
  await axios
    .get("../myCars.json") //Replaced by ("http://host:port/cars")
    .then((response) => {
      carsData.value = response.data.cars; // delete (.cars)
    })
    .catch((err) => {
      alert("Ошибка подключения к базе данных. Данные недоступны.");
      console.log("Database connection error. Data is not available.");
    });
  return carsData;
}); */
const carsData = localDataCars.cars;

//Data (Brand, Model) from CarBrands.vue received via App.vue
const props = defineProps({
  msgData: Object,
});

const showOverlay = ref(false);
const idSelectedItem = ref();
</script>

<template>
  <section class="list">
    <div class="container">
      <div class="list__items">
        <h2 class="list__title">Выбор авто</h2>
        <div
          class="list__items-cars"
          v-if="props.msgData.brand == '' && props.msgData.model == ''"
        >
          <a
            :id="cars.id"
            @click="
              (idSelectedItem = $event.target.id.replace(/[^0-9\.]+/g, '')),
                (showOverlay = true)
            "
            class="list__items-cars-item"
            v-for="cars in carsData"
            :key="cars.id"
            ref="test"
          >
            <img
              :id="`img-` + cars.id"
              class="list__items-cars-item-img"
              :src="`images/${cars.id}/${cars.photo.img1}`"
              alt="Авто_1"
            />
            <h3 :id="`subtitle-` + cars.id" class="list__items-cars-item-subtitle">
              {{ cars.brand }} {{ cars.model }}
            </h3>
            <p
              :id="`specifications-` + cars.id"
              class="list__items-cars-item-specifications"
            >
              {{ cars.engine }}, {{ cars.transmission }}, {{ cars.release }}
            </p>
            <p :id="`price-` + cars.id" class="list__items-cars-item-price">
              {{ cars.price }} &#8381;
            </p>
          </a>
        </div>
        <div class="list__items-cars" v-else-if="props.msgData.model == ''">
          <a
            :id="cars.id"
            class="list__items-cars-item"
            @click="
              (idSelectedItem = $event.target.id.replace(/[^0-9\.]+/g, '')),
                (showOverlay = true)
            "
            v-for="cars in (arr = carsData.filter(
              (cars) => cars.brand == props.msgData.brand
            ))"
            :key="cars.id"
          >
            <img
              :id="`img-` + cars.id"
              class="list__items-cars-item-img"
              :src="`images/${cars.id}/${cars.photo.img1}`"
              alt="Авто_1"
            />
            <h3 :id="`subtitle-` + cars.id" class="list__items-cars-item-subtitle">
              {{ cars.brand }} {{ cars.model }}
            </h3>
            <p
              :id="`specifications-` + cars.id"
              class="list__items-cars-item-specifications"
            >
              {{ cars.engine }}, {{ cars.transmission }}, {{ cars.release }}
            </p>
            <p :id="`price-` + cars.id" class="list__items-cars-item-price">
              {{ cars.price }} &#8381;
            </p>
          </a>
        </div>
        <div class="list__items-cars" v-else>
          <a
            :id="cars.id"
            class="list__items-cars-item"
            @click="
              (idSelectedItem = $event.target.id.replace(/[^0-9\.]+/g, '')),
                (showOverlay = true)
            "
            v-for="cars in (arr = carsData.filter(
              (cars) =>
                cars.brand == props.msgData.brand && cars.model == props.msgData.model
            ))"
            :key="cars.id"
          >
            <img
              :id="`img-` + cars.id"
              class="list__items-cars-item-img"
              :src="`images/${cars.id}/${cars.photo.img1}`"
              alt="Авто_1"
            />
            <h3 :id="`subtitle-` + cars.id" class="list__items-cars-item-subtitle">
              {{ cars.brand }} {{ cars.model }}
            </h3>
            <p
              :id="`specifications-` + cars.id"
              class="list__items-cars-item-specifications"
            >
              {{ cars.engine }}, {{ cars.transmission }}, {{ cars.release }}
            </p>
            <p :id="`price-` + cars.id" class="list__items-cars-item-price">
              {{ cars.price }} &#8381;
            </p>
          </a>
        </div>
      </div>
    </div>
    <ListCarsOverlay
      :show="showOverlay"
      :itemId="idSelectedItem"
      :carsData="carsData"
      @close="showOverlay = false"
    />
  </section>
</template>
