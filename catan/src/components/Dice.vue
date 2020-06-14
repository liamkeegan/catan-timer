<template>
  <div>
    <div class="dice first-face" v-if="activeRoll == 0">
    </div>
    <div class="dice first-face" v-if="activeRoll == 1">
      <span class="dot"> </span>
    </div>

    <div class="dice second-face" v-if="activeRoll == 2">
      <span class="dot"> </span>
      <span class="dot"> </span>
    </div>

    <div class="dice third-face" v-if="activeRoll == 3">
      <span class="dot"></span>
      <span class="dot"></span>
      <span class="dot"></span>
    </div>

    <div class="dice fourth-face" v-if="activeRoll == 4">
      <div class="column">
        <span class="dot"></span>
        <span class="dot"></span>
      </div>
      <div class="column">
        <span class="dot"></span>
        <span class="dot"></span>
      </div>
    </div>

    <div class="fifth-face dice" v-if="activeRoll == 5">
      <div class="column">
        <span class="dot"></span>
        <span class="dot"></span>
      </div>

      <div class="column">
        <span class="dot"></span>
      </div>

      <div class="column">
        <span class="dot"></span>
        <span class="dot"></span>
      </div>
    </div>

    <div class="dice fourth-face" v-if="activeRoll == 6">
      <div class="column">
        <span class="dot"></span>
        <span class="dot"></span>
        <span class="dot"></span>
      </div>
      <div class="column">
        <span class="dot"></span>
        <span class="dot"></span>
        <span class="dot"></span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    activeRoll: {
      type: Number,
      required: true,
    },
  },
};
</script>

<style>
/* Intial setup for displaying things in center */

body {
  display: flex;
  align-items: center;
  justify-content: center;
  vertical-align: center;
  flex-wrap: wrap;
  align-content: center;
  font-family: "Open Sans", sans-serif;

  background: linear-gradient(top, #222, #333);
}

/* code starts here */

.first-face {
  display: flex;
  justify-content: center;
  align-items: center;
}
.dice {
  padding: 4px;
  background-color: tomato;
  width: 104px;
  height: 104px;
  border-radius: 10%;
  margin-right: 10px;
}
.dot {
  display: block;
  width: 24px;
  height: 24px;
  border-radius: 50%;
  background-color: white;
}

.second-face {
  display: flex;
  justify-content: space-between;
}

.second-face .dot:nth-of-type(2) {
  align-self: flex-end;
}

.third-face {
  display: flex;
  justify-content: space-between;
}

.third-face .dot:nth-of-type(1) {
  align-self: flex-end;
}

.third-face .dot:nth-of-type(2) {
  align-self: center;
}

.fourth-face,
.sixth-face,
.fifth-face {
  display: flex;
  justify-content: space-between;
}

.fourth-face .column,
.sixth-face .column,
.fifth-face .column {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.fifth-face .column:nth-of-type(2) {
  justify-content: center;
}
</style>
