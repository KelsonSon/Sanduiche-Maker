<template>
  <div>
    <SandBoard />
  </div>
</template>

<script>
import SandBoard from "./components/SandBoard.vue";

export default {
  name: "App",
  components: {
    SandBoard,
  },
  
};
</script>

<style>
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
body{
  background-image: url('../public/img/background.jpg');
}
:root{
  --primary-color: #D93D04;
  --secondary-color: #F28705;
  --tertiary-color: #6E8C03;
  --white-color: #ffffff;
  --white-color-aa: #f2f2f2aa;
  --black-color: #333333;
  --bg-color: #703E1D;
}
</style>
