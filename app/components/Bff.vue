<script setup lang="ts">
import { Button } from "@repo/ui";
import BannerForFooter from "~/assets/images/bff.jpg";
</script>

<template>
  <article class="block">
    <img class="banner-img" :src="BannerForFooter" alt="sale banner" />
    <div class="overlay">
      <h2 class="title">Big Summer Sale</h2>
      <h3 class="subtitle">Commodo fames vitae vitae leo mauris in. Eu consequat.</h3>
      <Button label="Shop Now" class="button" small variant="stroke" color="white"/>
    </div>
  </article>
</template>

<style scoped>
.block {
  position: relative;
  width: 100%;
}

.banner-img {
  display: block;
  width: 100%;
  height: auto;
}

.overlay {
  position: absolute;
  inset: 0;
  z-index: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 16px;
  padding: 40px 16px;
  text-align: center;
}

.title {
  font-size: 70px;
  color: white;
  margin: 0;
}

.subtitle {
  font-size: 18px;
  color: white;
  font-weight: 400;
  max-width: 500px;
  margin: 0;
}

.button {
  margin-top: 8px;
}
</style>
