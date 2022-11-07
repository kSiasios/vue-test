<template>
  <Login :style="cssProps" />
</template>

<script>
import Login from "./Login.vue";

export default {
  name: "App",
  components: { Login },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Dosis:wght@200;300;400;500;700;800&display=swap");
@import "./styles/global.css";

* {
  font-family: Dosis, sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
