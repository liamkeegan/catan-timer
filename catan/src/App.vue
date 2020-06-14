<template>
  <div id="app">
    <b-container class="mx-auto">
      <b-row class="justify-content-md-center" align-v="center">
        <b-col>
          <dice :activeRoll=d1></dice>
        </b-col>
        <b-col>
          <dice :activeRoll=d2></dice>
        </b-col>
        <b-col>
          <timer :time-left="formattedTimeLeft"></timer>
        </b-col>
      </b-row>
      <b-row>
        <b-col><b-button size="lg" v-on:click="rollDice">Roll!</b-button></b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import Dice from "./components/Dice.vue";
import Timer from "./components/Timer.vue";

export default {
  name: "App",
  components: {
    Dice,
    Timer,
  },
  data() {
    return {
      timeLimit: 0,
      timePassed: 0,
      timerInterval: null,
      d1: 0,
      d2: 0
    };
  },
  computed: {
    formattedTimeLeft() {
      const timeLeft = this.timeLeft;
      // The largest round integer less than or equal
      //   to the result of time divided being by 60.
      const minutes = Math.floor(timeLeft / 60);
      // Seconds are the remainder of the time divided
      //   by 60 (modulus operator)
      let seconds = timeLeft % 60;
      // If the value of seconds is less than 10,
      //   then display seconds with a leading zero
      if (seconds < 10) {
        seconds = `0${seconds}`;
      }
      // The output in MM:SS format
      return `${minutes}:${seconds}`;
    },
    timeLeft() {
      return this.timeLimit - this.timePassed;
    },
  },
  methods: {
    rollDice() {
      
      this.timeLimit = 120,
      this.timePassed = 0,
      clearInterval(this.timerInterval);

      this.timerInterval = setInterval(() => (this.timePassed += 1), 1000);
      this.d1 = Math.floor( Math.random() * 6 ) +1;
      this.d2 = Math.floor( Math.random() * 6 ) +1;
    }
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
