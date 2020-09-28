<template>
  <section class="restaurantinfo">
    <div v-for="restaurant in foodData" :key="restaurant.id">
      <h2>{{ restaurant.name }}</h2>
      <p>Delivery Time {{ restaurant.deliveryTime }}</p>
      <p>Rating {{ restaurant.rating }}</p>
      <p v-if="restaurant.freeDelivery" class="label">
        <span>Free Delivery!</span>
      </p>

      <div class="row">
        <div
          v-for="menuItem in restaurant.menu"
          :key="menuItem.id"
          class="items"
          :style="`background: url(${menuItem.img}) no-repeat center center`"
        >
          <div class="iteminfo">
            <div>
              <h4>{{ menuItem.item }}</h4>
              <p>$ {{ menuItem.price.toFixed(2) }}</p>
            </div>

            <button class="ghost">View Item</button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { mapState } from "vuex";

export default {
  computed: {
    ...mapState(["foodData"])
  }
};
</script>

<style lang="scss" scoped></style>
