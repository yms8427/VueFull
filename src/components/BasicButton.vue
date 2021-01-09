<template>
  <button class="btn c-button mr-2 ml-2" :class="mainClass">
    <i v-if="font" :class="font"></i>
    <slot></slot>
  </button>
</template>

<script>
const VARIANTS = ["primary", "danger", "warning", "default"];
export default {
  name: "basic-button",
  props: {
    variant: {
      type: String,
      default: "default",
      validator: function(value) {
        return VARIANTS.indexOf(value) > -1;
      },
    },
    font: {
      type: String,
    },
  },
  computed: {
    mainClass: function() {
      return "btn-" + this.variant;
    },
  },
};
</script>

<style scoped>
.c-button {
  min-width: 150px;
  height: 40px;
}
</style>
