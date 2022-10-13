<template>
  <div @click="showLetter" class="letter">
    <span :style="spanStyles">{{ letter }}</span>
  </div>
</template>

<script>
export default {
  name: "Button",
  props: {
    letter: String,
    hideContent: {
      type: Boolean,
      default: false,
    },
  },
  computed: {
    spanStyles() {
      const display = this.hideContent ? "none" : "block";
      return `display: ${display}`;
    },
  },
  methods: {
    showLetter() {
      this.$emit("show-letter", this.letter);
    },
  },
};
</script>
