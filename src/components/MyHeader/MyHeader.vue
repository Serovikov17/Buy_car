<script setup>
import { ref } from "vue";
import InfoOverlay from "./InfoOverlay.vue";

const showInfo = ref(false);
</script>
<template>
  <div class="container">
    <div class="header__header">
      <div class="header__header-logo"><span>ЛОГОТИП</span></div>
      <nav class="header__header-menu">
        <a class="header__header-menu-link" @click="showInfo = true">
          О нас / Контакты
        </a>
      </nav>
    </div>
  </div>
  <InfoOverlay :showInfoOwerlay="showInfo" @closeInfo="showInfo = false" />
</template>
