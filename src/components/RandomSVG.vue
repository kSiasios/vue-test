<template>
  <img
    class="svg-image"
    :src="'/assets/svg/' + type + 's/' + type + '-' + svgNum + '.svg'"
    alt="Pet related image"
    :style="cssProps"
  />
</template>

<script>
export default {
  name: "RandomSVG",
  props: {
    type: String,
    svgNum: String,
    opacity: { type: String, default: "1" },
  },
  computed: {
    cssProps() {
      return {
        "--opacity": this.opacity,
      };
    },
  },
};
</script>

<style scoped>
.svg-image {
  width: 100%;
  aspect-ratio: 1;
  opacity: var(--opacity);
}
</style>
