<template>
  <div id="app">
    <HelloWorld msg/>
    <CsButton label />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import CsButton from "./components/CsButton ";
export default {
  name: "App",
  components: {
    HelloWorld,
    CsButton,
  },

  data: function () {
    return {};
  },

  methods: {},
};
</script>

<style>
#app {
  font-family: "Metal Mania", cursive;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: px;
}
body {
  background: url(https://media3.giphy.com/media/xT8pesqN65dsFw18Hu/giphy.gif);
  background-attachment: fixed;
  background-repeat: no-repeat;
  background-size: 100% 100%;
  height: 100vh;
}
</style>
