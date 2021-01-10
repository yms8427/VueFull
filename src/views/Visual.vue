<template>
  <div class="text-center mt-5">
    <div class="row">
      <div class="col-md-12">
        <button class="btn btn-dark mr-2" @click="makeNight">Gece</button>
        <button class="btn btn-warning text-light" @click="makeDay">
          Gündüz
        </button>
      </div>
    </div>
    <div class="row" :class="{ night: mode === 'night', day: mode === 'day' }">
      <div class="col-md-12">
        <house ref="house" />
      </div>
    </div>
  </div>
</template>

<script>
import House from "../components/House";
export default {
  name: "Visual",
  components: {
    House,
  },
  data: () => ({
    mode: "day",
  }),
  methods: {
    makeNight() {
      this.mode = "night";
      this.$refs.house.turnOnLights();
    },
    makeDay() {
      this.mode = "day";
      this.$refs.house.turnOffLights();
    },
  },
};
</script>

<style scoped>
.night {
  background-color: #666;
  transition: 3s;
}
.day {
  background-color: rgb(116, 182, 243);
  transition: 3s;
}
</style>
