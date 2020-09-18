<template>
  <div id="app">
    <Calculator />
  </div>
</template>

<script>
import Calculator from "./components/Calculator.vue";

export default {
  name: "App",
  components: {
    Calculator,
  },
};
</script>

<style>
html,
body {
  height: 100%;
  width: 100%;
  background: linear-gradient(73deg, #56d50f, #c6490f);
  background-size: 400% 400%;

  -webkit-animation: AnimationName 29s ease infinite;
  -moz-animation: AnimationName 29s ease infinite;
  animation: AnimationName 29s ease infinite;
}
@-webkit-keyframes AnimationName {
  0% {
    background-position: 0% 17%;
  }
  50% {
    background-position: 100% 84%;
  }
  100% {
    background-position: 0% 17%;
  }
}
@-moz-keyframes AnimationName {
  0% {
    background-position: 0% 17%;
  }
  50% {
    background-position: 100% 84%;
  }
  100% {
    background-position: 0% 17%;
  }
}
@keyframes AnimationName {
  0% {
    background-position: 0% 17%;
  }
  50% {
    background-position: 100% 84%;
  }
  100% {
    background-position: 0% 17%;
  }
}
@font-face {
  font-family: digital-7;
  src: local("digital-7"), url(./fonts/digital-7.ttf) format("truetype");
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
