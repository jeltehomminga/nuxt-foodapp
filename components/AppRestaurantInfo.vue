<template>
  <section class="restaurantinfo">
    <div v-for="restaurant in filteredRestaurants" :key="restaurant.id">
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
            <nuxt-link :to="`/items/${menuItem.id}`">
              <button class="ghost">View Item</button></nuxt-link
            >
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    filteredRestaurants: {
      type: [Array, Object],
      default: () => []
    }
  }
};
</script>

<style lang="scss" scoped></style>
