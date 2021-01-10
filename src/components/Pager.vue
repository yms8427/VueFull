<template>
  <div class="float-right">
    <button class="btn btn-sm btn-primary mr-2" @click="previous">
      {{ previousText }}
    </button>
    <button class="btn btn-sm btn-primary" @click="next">{{ nextText }}</button>
  </div>
</template>

<script>
export default {
  name: "Pager",
  props: {
    nextText: {
      type: String,
      default: "Next",
    },
    previousText: {
      type: String,
      default: "Previous",
    },
  },
  methods: {
    next() {
      this.$emit("on-next");
    },
    previous() {
      this.$emit("on-previous");
    },
  },
};
</script>

<style scoped>
button {
  min-width: 100px;
}
</style>
