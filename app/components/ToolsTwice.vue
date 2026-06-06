<script setup lang="ts">
import { ProductCard } from "@repo/ui";

import iphoneGold from "~/assets/images/products/apple_gold_iphone.png";
import airPodsImage from "~/assets/images/products/airpods_max.png";
import appleWatch from "~/assets/images/products/apple_watch.png";
import iphoneWhite from "~/assets/images/products/apple_white_iphone.png";

const products = [
  {
    cardname: "Apple iPhone 14 Pro 512GB Gold (MQ233)",
    price: "1437",
    image: iphoneGold,
    favorite: false
  },
  {
    cardname: "AirPods Max Silver",
    price: "549",
    image: airPodsImage,
    favorite: false
  },
  {
    cardname: "Apple Watch Series 9 GPS 41mm Starlight Aluminium Case",
    price: "399",
    image: appleWatch,
    favorite: false
  },
  {
    cardname: "Apple iPhone 14 Pro 1TB Gold (MQ2V3)",
    price: "1499",
    image: iphoneWhite,
    favorite: false
  },
];

</script>
<template>
  <article class="wrapper">
  <header class="header">
    <div class="hd">
      <h2>Discounts up to -50%</h2>
    </div>
  </header>
  <section class="items-grid">
    <ProductCard
      v-for="(product, index) in products"
      :title="product.cardname"
      :currentPrice="Number(product.price)"
      :image="product.image"
      :id="index"
      :inCart="false"
      :wide="false"
    />
  </section>
  </article>
</template>

<style scoped>

.wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  
}

.header {
  width: 100%;
  max-width: 1150px;
  text-align: left;
  padding-bottom: 15px;
}

.hd {
  display: flex;
  gap: 16px;
  cursor: pointer;
}

.items-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
  justify-content: center;
  justify-items: center;
    font-size: 30px;
}

@media (min-width: 600px) {
  .wrapper {
    padding: 48px 160px;
  }

  .items-grid {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 32px;
  }
}

</style>