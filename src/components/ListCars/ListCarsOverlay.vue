<script setup>
import { ref } from "vue";
import VuePictureSwipe from "vue3-picture-swipe"; //Gallery plugin

const props = defineProps({
  show: Boolean,
  itemId: String,
  carsData: Object,
});
</script>

<template>
  <div class="list__overlay" :class="{ overlayListOn: props.show }">
    <div class="container">
      <div
        class="list__overlay-window"
        v-for="car in (arrItem = props.carsData.filter(
          (item) => item.id == props.itemId
        ))"
        :key="car.id"
      >
        <div class="list__overlay-window-close">
          <button @click="$emit('close')">Закрыть</button>
        </div>
        <div class="list__overlay-window-gallery">
          <vue-picture-swipe
            :items="[
              {
                src: `images/${car.id}/${car.photo.img1}`,
                thumbnail: `images/${car.id}/${car.photo.img1}`,
                w: 1200,
                h: 900,
              },
              {
                src: `images/${car.id}/${car.photo.img2}`,
                thumbnail: `images/${car.id}/${car.photo.img2}`,
                w: 1200,
                h: 900,
              },
              {
                src: `images/${car.id}/${car.photo.img3}`,
                thumbnail: `images/${car.id}/${car.photo.img3}`,
                w: 1200,
                h: 900,
              },
              {
                src: `images/${car.id}/${car.photo.img4}`,
                thumbnail: `images/${car.id}/${car.photo.img4}`,
                w: 1200,
                h: 900,
              },
              {
                src: `images/${car.id}/${car.photo.img5}`,
                thumbnail: `images/${car.id}/${car.photo.img5}`,
                w: 1200,
                h: 900,
              },
            ]"
          ></vue-picture-swipe>
        </div>
        <hr />
        <div class="list__overlay-window-specifications">
          <div class="list__overlay-window-specifications-name">
            <h3>{{ car.brand }} {{ car.model }}</h3>
          </div>
          <div class="list__overlay-window-specifications-info">
            <p>
              Год выпуска: <span>{{ car.release }}</span>
            </p>
            <p>
              Пробег, км: <span>{{ car.mileage }}</span>
            </p>
            <p>
              ПТС: <span>{{ car.pts }}</span>
            </p>
            <p>
              Владельцев ПТС: <span>{{ car.owner }}</span>
            </p>
            <p>
              Состояние: <span>{{ car.сondition }}</span>
            </p>
            <p>
              Модификация:
              <span>{{ car.engine }} {{ car.transmission }} ({{ car.power }} л.с.)</span>
            </p>
            <p>
              Объём двигателя: <span>{{ car.engine }}</span>
            </p>
            <p>
              Тип двигателя: <span>{{ car.engine_type }}</span>
            </p>
            <p>
              Коробка передач: <span>{{ car.transmission }}</span>
            </p>
            <p>
              Привод: <span>{{ car.drive }}</span>
            </p>
            <p>
              Комплектация: <span>{{ car.equipment }}</span>
            </p>
            <p>
              Тип кузова: <span>{{ car.body_type }}</span>
            </p>
            <p>
              Цвет: <span>{{ car.colour }}</span>
            </p>
            <p>
              Руль: <span>{{ car.wheel }}</span>
            </p>
          </div>
        </div>
        <hr />
        <div class="list__overlay-window-description">
          <p>
            Описание: <span>{{ car.description }}</span>
          </p>
        </div>
        <hr />
        <div class="list__overlay-window-phone">
          <p>СВЯЗАТЬСЯ С НАМИ:</p>
          <p>
            <a href="tel:83422076190">+7 (342) 207-61-90</a>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>
