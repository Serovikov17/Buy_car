<script setup>
import { ref } from "vue";

const props = defineProps({
  showInfoOwerlay: Boolean,
});
</script>

<template>
  <div class="information">
    <div class="information__overlay" :class="{ overlayInfoOn: props.showInfoOwerlay }">
      <div class="container">
        <div class="information__overlay-window">
          <div class="information__overlay-window-close">
            <button class="btn__close" @click="$emit('closeInfo')">Закрыть</button>
          </div>
          <div class="information__overlay-window-description">
            <div class="information__overlay-window-description-company">
              <h3>Компания:</h3>
              <p>ОБЩЕСТВО С ОГРАНИЧЕННОЙ ОТВЕТСТВЕННОСТЬЮ "Наименование компании"</p>
              <p>Директор - Иванов Иван Иванович</p>
              <p>ОГРН — 0000000000000</p>
              <p>ИНН — 5904900000</p>
              <p>КПП — 590000000</p>
              <p>Юридический адрес — 614025, Пермский край, г Пермь</p>
              <p>Расчетный счет — 40002000200070001000</p>
              <p>Название банка — Волго-Вятский банк ПАО СБЕРБАНК</p>
              <p>БИК — 04 - - - - - 03</p>
              <p>Корреспондентский счет банка — 30101000000000000003</p>
              <div>
                <h3>Фактический адрес:</h3>
                <p>614066, г Пермь, ул. Рязанская, ...</p>
              </div>
            </div>
            <hr />
            <div class="information__overlay-window-description-managers">
              <h3>Контактные лица / Телефоны</h3>
              <div class="information__overlay-window-description-managers-contacts">
                <div
                  class="information__overlay-window-description-managers-contacts-names"
                >
                  <p>Сегей</p>
                  <p>Андрей</p>
                  <p>Антон</p>
                  <p>Роман</p>
                </div>
                <div
                  class="information__overlay-window-description-managers-contacts-phone"
                >
                  <p><a href="tel:83422076190">+7 (342) 000-00-00</a></p>
                  <p><a href="tel:83422076190">+7 (342) 000-00-00</a></p>
                  <p><a href="tel:83422076190">+7 (342) 000-00-00</a></p>
                  <p><a href="tel:83422076190">+7 (342) 000-00-00</a></p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
