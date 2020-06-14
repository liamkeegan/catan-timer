<template>
  <div class="base-timer">
    <span class="base-timer__label">
      {{ timeLeft }}
    </span>
  </div>
</template>

<script>
export default {
  props: {
    timeLeft: {
      type: Number,
      required: true,
    },
  },
};
</script>

<style scoped lang="scss">
/* Sets the containers height and width */
.base-timer {
  position: relative;
  width: 300px;
  height: 300px;
  /* Removes SVG styling that would hide the time label */
  &__label {
    position: absolute;

    /* Size should match the parent container */
    width: 300px;
    height: 300px;
    /* Keep the label aligned to the top */
    top: 0;
    /* Create a flexible box that centers content vertically and horizontally */
    display: flex;
    align-items: center;
    justify-content: center;
    /* Sort of an arbitrary number; adjust to your liking */
    font-size: 48px;
  }
}
</style>
