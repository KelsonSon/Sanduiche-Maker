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
  background-size: cover;
  background-repeat: no-repeat;
}
:root{
  --primary-color: #D93D04;
  --secondary-color: #ffffff;
  --tertiary-color: #333333aa;
  --white-color: #ffffff;
  --white-color-aa: #f2f2f2aa;
  --black-color: #333333;
  --bg-color: #703E1D;
}

@media (max-width: 768px) {
    .container {
      width: 100%;
    }

    .text {
      font-size: 16px;
    }

    .button {
      width: 100px;
    }
  }
</style>
