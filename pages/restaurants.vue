<template>
  <main class="container restaurant">
    <div class="restaurantheading">
      <h1>Restaurants</h1>
      <AppSelect @change="selectedRestaurant = $event" />
      <pre>{{ $data }}</pre>
    </div>

    <AppRestaurantInfo :filteredRestaurants="filteredRestaurants" />
  </main>
</template>

<script>
import AppRestaurantInfo from "@/components/AppRestaurantInfo.vue";
import AppSelect from "@/components/AppSelect.vue";
import { mapState } from "vuex";

export default {
  components: {
    AppRestaurantInfo,
    AppSelect
  },
  data() {
    return {
      selectedRestaurant: ""
    };
  },
  computed: {
    ...mapState(["foodData"]),
    filteredRestaurants() {
      if (this.selectedRestaurant) {
        return this.foodData.filter(({ name }) =>
          name.toLowerCase().includes(this.selectedRestaurant)
        );
      }
    }
  }
};
</script>

<style lang="scss" scoped></style>
