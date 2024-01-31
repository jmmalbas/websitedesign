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
  color: rgb(31, 228, 250);
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
  background: rgba(255, 255, 255, 0.7) url('https://img.freepik.com/free-vector/worldwide-connection-blue-background-illustration-vector_53876-76826.jpg?w=1380&t=st=1706417840~exp=1706418440~hmac=8f5e49608254d1d0525f522a7aaee378db1e6139bc45cdcd2c849430143d0505') no-repeat center center fixed;
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
