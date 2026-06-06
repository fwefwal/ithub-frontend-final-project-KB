<script setup lang="ts">
import { ProductCard } from "@repo/ui";

import iphoneSilver from "~/assets/images/products/apple_silver_iphone.png";
import blackmagicCamera from "~/assets/images/products/niko_camera.png";
import appleWatch from "~/assets/images/products/apple_watch.png";
import airPodsImage from "~/assets/images/products/airpods_max.png";
import samsungWatch from "~/assets/images/products/samsung_watch.png";
import galaxyPhone from "~/assets/images/products/samsung_galaxy.png";
import galaxyHeadphones from "~/assets/images/products/samsung_headphones.png";
import appleIpad from "~/assets/images/products/apple_ipad.png";


const products = [
  {
    cardname: "Apple iPhone 14 Pro Max 128GB Deep Purple (MQ9T3RX/A)",
    price: "900",
    image: iphoneSilver,
    favorite: false
  },
  {
    cardname: "Blackmagic Pocket Cinema Camera 6k",
    price: "2535",
    image: blackmagicCamera,
    favorite: false
  },
  {
    cardname: "Apple Watch Series 9 GPS 41mm Starlight Aluminium Case",
    price: "399",
    image: appleWatch,
    favorite: false
  },
  {
    cardname: "AirPods Max Silver",
    price: "549",
    image: airPodsImage,
    favorite: false
  },
  {
    cardname: "Samsung Galaxy Watch6 Classic 47mm Black",
    price: "369",
    image: samsungWatch,
    favorite: false
  },
  {
    cardname: "Galaxy Z Fold5 Unlocked | 256GB | Phantom Black",
    price: "1799",
    image: galaxyPhone,
    favorite: true
  },
  {
    cardname: "Galaxy Buds FE Graphite",
    price: "99.99",
    image: galaxyHeadphones,
    favorite: false
  },
  {
    cardname: "Apple iPad 9 10.2` 64GB Wi-Fi Silver (MK2L3) 2021",
    price: "398",
    image: appleIpad,
    favorite: false
  },
];

</script>
<template>
  <article class="wrapper">
  <header class="header">
    <div class="hd">
      <h4>New Arrival</h4>
      <h4>Bestseller</h4>
      <h4>Featured Products</h4>
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

.hd h4:first-child {
  text-decoration: underline;
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