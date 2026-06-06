<script lang="ts" setup>
import { ProductCard, CartPrice } from "@repo/ui";
import { Field} from "@repo/ui";
import { useCartLocal } from "~/stores/cartLocal";
import { useCart } from "~/stores/cart";

import airpodsMaxImage from "~/assets/images/products/airpods_max.png";
import Button from "../../../../packages/ui/src/components/Button.vue";

const { loggedIn } = useUserSession();

const cart = loggedIn ? useCart() : useCartLocal();
</script>

<template>
  <main class="page">
    <h2 class="page-title">Shopping Cart</h2>

    <section class="products-grid" v-if="cart?.items?.length">
      <div class="product-wrapper" v-for="product in cart.items">
        <ProductCard
          class="product-item"
          :title="product.title"
          :currentPrice="product.currentPrice"
          :id="product.id"
          :key="product.id"
          :image="airpodsMaxImage"
          wide
        />
        <CartPrice 
          :key="product.id"
          :quantity="product.quantity" 
          :currentPrice="product.currentPrice" 
          @decrement="cart.changeQuantity({
            ...product,
            quantity: product.quantity - 1
          })"
          @increment="cart.changeQuantity({
            ...product,
            quantity: product.quantity + 1
          })"
          @delete="cart.changeQuantity({
            ...product,
            quantity: 0
          })"
        />
      </div>
    </section>

    <section v-else>
      <p>You don't have any products in cart yet...</p>
    </section>

    <section class="order">
    <div>
      <h3 class="order-title">Order Summary</h3>
      <form action="" class="order-form" method="post">
      <Field label="Discount code / Promo code" placeholder="Code" class="code-field" />
  <Field label="Your bonus card number" placeholder="Enter Card Number">
    <template #right>
      <Button label="Apply" small variant="stroke" color="black"/>
    </template>
  </Field>
      <!-- <btton label="Apply"/> -->
<h4 class="priceline">Subtotal <span>{{ cart.subTotal }}</span></h4>
<h5 class="priceline">Estimated Tax <span>{{ cart.orderDetails.tax }}</span></h5>
<h5 class="priceline">Estimated shipping & Handling <span>{{ cart.orderDetails.shipping }}</span></h5>
<h4 class="priceline">Total <span>{{ cart.total }}</span></h4>
      <Button label="Checkout"></Button>
    </form>
    <!-- <h2></h2> -->
    <!-- <textarea></textarea> -->
    </div>
    </section>
  </main>
</template>

<style scoped>
/* .cuss {
  font-size: 1000px;
  margin:  100px;
} */

.order {
  max-width: 600px;
  border: 1px solid rgb(206, 206, 206);
  border-radius: 9px;
  padding: 50px 50px;
}

.order-form {
  display: flex;
  flex-direction: column;
  gap: 30px;
}

.order-title {
margin-bottom: 40px;
}

.page {
  flex: 1;
  padding: 40px 17px;
  display: flex;
  flex-direction: column;
  gap: 40px;
}

.page-title {
  font-size: 24px;
  line-height: 32px;
}

.priceline {
  display: flex;
  justify-content: space-between;
  width: 100%;
}

.products-grid {
  display: flex;
  flex-direction: column;
  gap: 40px;
}
</style>
