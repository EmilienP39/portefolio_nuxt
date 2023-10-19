<template>
  <footer class="footer">
    <p>&copy;2023 Emilien PAUL | All Rights Reserved</p>
  </footer>
</template>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@200;300;400;500;600;700;800;900&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Poppins", sans-serif;
}

body {
  display: flex;
  background: #333;
  justify-content: flex-end;
  align-items: flex-end;
  min-height: 100vh;
}

.footer {
  margin-top: 150px;
  position: relative;
  width: 100%;
  background-image:url("assets/color-sharp.png");
  background-size: cover;
  background-repeat: round;
  min-height: 100px;
  padding: 20px 50px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

</style>
