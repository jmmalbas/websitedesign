<script setup>
const client = useSupabaseClient();
const email = ref("");
const password = ref(null);
const errorMessage = ref(null);
const successMsg = ref("");

async function signUp() {
  try {
    const { data, error } = await client.auth.signUp({
      email: email.value,
      password: password.value,
    });
    if (error) {
      throw error;
    } else {
            successMsg.value = 'Check your email to confirm your account!';
      errorMessage.value = '';  
    }
  } catch (error) {
    errorMessage.value = error.message;
    successMsg.value = '';  
  }
}
</script>

<template>
  <div class="signup-form">
    <form @submit.prevent="signUp">
      <h3><strong class="register">Register</strong></h3>

      
      <div v-if="!successMsg">
        <label for="email">Email:</label>
        <input type="email" id="email" v-model="email" required />

        <label for="password">Password:</label>
        <input type="password" id="password" v-model="password" required />

        <button type="submit">Signup</button>
      </div>

      
      <div v-if="successMsg" class="success-message">
        {{ successMsg }}
      </div>
    </form>

    
    <div v-if="errorMessage" class="error-message">
      {{ errorMessage }}
    </div>

    <nav class="navbar">
      <div class="buttons">
        <NuxtLink to="/" class="nav-button">Home</NuxtLink>
        <NuxtLink to="/login" class="nav-button">Log In</NuxtLink>
      </div>
    </nav>
  </div>
</template>

<style scoped>

.register {
  font-size: 20px;
  color: rgb(7, 7, 7);
}

.success-message {
  color: rgb(250, 251, 251);
  margin-top: 10px;
  text-align: center;
  
}

.error-message {
  color: red; 
  margin-top: 10px;
  text-align: center;
}
.signup-form {
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

form {
  max-width: 400px;
  margin: 20px auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 10px;
}

h3,
label,
input,
button {
  color: white; 
}

h3 {
  text-align: center;
}

label {
  display: block;
  margin-top: 10px;
}

input {
  width: 100%;
  padding: 8px;
  margin-top: 10px;
  box-sizing: border-box;
  color: black; 
}

input:focus {
  color: black; 
}

button {
  background-color: #007bff;
  color: #fff;
  padding: 10px 20px;
  cursor: pointer;
  border: none;
  margin-top: 10px; 
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
.nav-button {
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
.signup-button:hover {
  background-color: #eee; 
}
</style>
