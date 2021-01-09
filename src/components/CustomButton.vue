<template>
  <button class="btn c-button mr-2 ml-2" :class="mainClass">
    <span class="mr-2">
      <slot name="before-icon"></slot>
    </span>
    <slot></slot>
    <span class="ml-2">
      <slot name="after-icon"></slot>
    </span>
  </button>
</template>

<script>
const VARIANTS = ["primary", "danger", "warning", "default"];
export default {
  name: "custom-button",
  props: {
    variant: {
      type: String,
      default: "default",
      validator: function(value) {
        return VARIANTS.indexOf(value) > -1;
      }
    }
  },
  computed: {
    mainClass: function() {
      return "btn-" + this.variant;
    }
  }
};
</script>

<style scoped>
.c-button {
  min-width: 150px;
  height: 40px;
}
</style>
