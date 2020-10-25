<template>
  <main class="container restaurant">
    <div class="restaurantheading">
      <h1>Restaurants</h1>

      <AppSelect @change="selectRestaurant = $event" />
    </div>

    <AppRestaurantInfo :datasource="filterRestaurant" />
  </main>
</template>

<script>
import AppRestaurantInfo from "@/components/AppRestaurantInfo.vue";
import AppSelect from "@/components/AppSelect.vue";
import { mapState } from "vuex";

export default {
  components: {
    AppRestaurantInfo,
    AppSelect,
  },
  data() {
    return {
      selectRestaurant: "",
    };
  },
  computed: {
    ...mapState(["fooddata"]),
    filterRestaurant() {
      if (this.selectRestaurant) {
        return this.fooddata.filter((el) => {
          let name = el.name.toLowerCase();
          return name.includes(this.selectRestaurant);
        });
      }
      return this.fooddata;
    },
  },
};
</script>

<style lang="scss" scoped>
</style>