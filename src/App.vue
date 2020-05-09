<template>
  <div id="app">
    <div class="main-container">
      <Nav />
      <Carousel />
      <div class="btnContainer">
        <button>View more</button>
      </div>
    </div>
  </div>
</template>

<script>
import Nav from "./components/Nav.vue"
import Carousel from "./components/Carousel.vue"
export default {
  name: "App",
  components: {
    Nav,
    Carousel,
  },
}
</script>

<style>
body {
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  justify-content: center;
  align-items: center;
  color: #2c3e50;
  background-color: #f4efe5;
  width: 100%;
  height: 100vh;
}

.main-container {
  width: 1145px;
  max-height: 684px;
  background-color: #ffffff;
  border-radius: 8px;
  box-shadow: 0px 0px 108px 12px rgba(241, 138, 117, 0.13);
}

.btnContainer {
  display: flex;
  justify-content: center;
  align-content: center;
  width: 100%;
  height: 65px;
  margin-top: 20px;
}

.btnContainer button {
  width: 160px;
  height: 49px;
  border-radius: 5px;
  background-color: #EB6649;
  font-size: 14px;
  color: #ffffff;
  border: none;
}

</style>
