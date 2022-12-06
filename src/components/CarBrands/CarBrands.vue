<script setup>
import { ref } from "vue";
import carsData from "../../data/carsBase-master/cars.json";

const carsArr = carsData.list; //Аrray with Brands and Models
const carsBrand = ref(Object.keys(carsArr));
const carsModel = ref(Object.values(carsArr));
const selectedBrand = ref("");
const selectedModel = ref("");
let newBrand = ref("");

//Switch the model to " " when choosing a new brand
function resetModel() {
  if (selectedBrand.value !== newBrand.value) {
    selectedModel.value = "";
    newBrand = selectedBrand.value;
  }
}

//Transferring the selected Brand and Model to App.vue
const emit = defineEmits(["response"]);
emit("response", {
  brand: selectedBrand,
  model: selectedModel,
});
</script>

<template>
  <section class="brands">
    <div class="container">
      <div class="brands__brand">
        <h2 class="brands__title">Выбор авто</h2>
        <div id="testT" class="brands__brand-item">
          <span class="brands__brand-item-brand-text">Выберите марку(бренд) авто:</span>
          <select
            name="brand"
            class="brands__brand-item-brand-choice"
            v-model="selectedBrand"
            @change="resetModel"
          >
            <option value=""></option>
            <option v-for="brand in carsBrand" :key="brand.id" :value="brand">
              {{ brand }}
            </option>
          </select>
          <span class="brands__brand-item-model-text">Выберите модель авто:</span>
          <select
            name="model"
            class="brands__brand-item-model-choice"
            v-model="selectedModel"
          >
            <option value=""></option>
            <option
              v-for="model in carsArr[selectedBrand]"
              :key="model.id"
              :value="model"
            >
              {{ model }}
            </option>
          </select>
        </div>
      </div>
    </div>
  </section>
</template>
