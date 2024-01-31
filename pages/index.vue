<template>
  <div class="welcome-page">
    <nav class="navbar">
      <div class="buttons">
        
        <NuxtLink to="/login" class="sign-button">Log In</NuxtLink>
        <NuxtLink to="/signup" class="sign-button">Sign Up</NuxtLink>
        
      </div>
    </nav>
    <div class="content-container">
      <h1 class="title"><strong>CPRG - 206</strong></h1>
      <h1 class="title"><strong>Database Web Integration</strong></h1>
      <div class="image-container">
        <img class="course-image" src="https://img.freepik.com/free-vector/illustration-social-media-concept_53876-18135.jpg?w=1060&t=st=1706246053~exp=1706246653~hmac=626caa7bcfd6466ffa003c31eee7873a461558e8562972b874fe3cb7d0528930" alt="Course Image">
      </div>
      <div class="textbox">
        <p class="description">
          Welcome to our dynamic website creation course! In this course, you will gain the
          knowledge and skills needed to build exciting and interactive websites. You'll
          learn the process of creating dynamic sites that pull content from a database.
          Additionally, you'll master the art of designing web interfaces for databases,
          allowing seamless data input without the need for HTML or database expertise.
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {

}
</script>

<style scoped>
.welcome-page {
  text-align: center;
  margin: auto;
  padding: 20px;
  background: rgba(255, 255, 255, 0.7) url('https://lh3.googleusercontent.com/pw/ABLVV861lwJ6BLppPj58uHfLnDEI1_U932rgRCX4azyTBSNsCU6vdJ4wsuhUgFYzeDLI89mvIPV5lQu4Q0NVjSIva4kn-0676P1iQLLDuqOzaO-2eycNozdqRpr8QbufNkYeg4ZLKPdC5PV6rFQIPGpjTBj-BL33pO7qlATLEJ3-0YPpWH7ehIxjR9QmpafAFOOy7pft3mvrZEU-ONcI4DVqIDBCFLLMN-moLZOza6v5wtpPYsRIsCfJMbsN0CGeKQAvR1oIprpm3f9zFug4Ln2X6J8uyB0ljSg2p6Pwe8v_3JgCx9Xbl49OY31g-jt4P6JYwj1n1UswC4G7tIyegk1lEXnK1hzUn2AUGFWcBdBR6oyFvdT4k9dfA7VCoAStOavnvlJ18ClZQ7P8dwP3yMOvzn56vdAjIsaaxAaFi95-c7YpgQqAJCC6j5HHOAofd_wgUBnhoK3Gr7_4zBrfeyCrg6cRaCMqUunJPWZz9OC4jYrnW7oP70hqtA6mvK89RqkyWPd0pw5pyzAP13c6ZiTKqBiFLg2qsPnxRu_ybb817rI-j1dVpNR7uNwylGraBdtv_xQ3EEkMsfHul5N8sMFdvdfNQPhoDq5WR7iDZaRxkUPZNjP4GUm1mWq_VQxLlOZZhEzoYQ5ikgwpmCfSmCxb-70NfFRX81LgkwsoWVfFcbVTWk7mjPqEVvV7HTT0lA-NLfMhqcikyHG0pjQzNJR4d9sdLPq_OorXGpgRg15siIpz_ueF1h_1eRXTK2ty6oKbMrZYDpR5fsOQWs7wPWxyKAN_ZXhhyTcAwFlWlBasGVyciN-xx_4mB6O6RgsdH89V6HOfBl9l1WcUE75oUPfzk4f-tQF00GDVZo50fwwIY2pFMCKxuThiWPorDvbAPKgt4lPLY3k4NRChNxp0ToKk6sS0=w1380-h862-s-no-gm?authuser=0') no-repeat center center fixed;
  background-size: cover;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  width: 100vw;
  background: rgba(255, 255, 255, 0.7); 
  padding: 8px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1); 
  margin: auto; 
  display: flex; 
  justify-content: flex-end; 
}

.buttons {
  margin-right: 30px; 
}

.login-button,
.sign-button {
  padding: 5px 30px;
  font-size: 1em;
  color: #333;
  background-color: #fff; 
  border: none;
  border-radius: 20px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.login-button:hover,
.sign-button:hover {
  background-color: #eee; 
}

.content-container {
  display: flex;
  flex-direction: column;
  gap: 5px;
}

.title {
  color: white;
  font-size: 3.4em;
  margin: 0;
  transition: color 0.3s ease;
}

.title:hover {
  color: black;
}

.image-container {
  overflow: hidden;
  border-radius: 10px;

  max-width: 30%;
  margin: auto;
}

.course-image {
  width: 100%;
  height: auto;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.course-image:hover {
  transform: scale(1.1);
}

.textbox {
  border-radius: 10px;
  padding: 20px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
  width: 560px; 
  margin: auto;
  background-color: rgba(255, 255, 255, 0.8);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.textbox:hover {
  transform: scale(1.05); 
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.3); 
}

.description {
  margin: 0;
  line-height: 1.6;
  font-size: 1.2em;
  color: #333;
  max-width: 100%;
}
</style>
