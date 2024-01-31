<script setup>
const user = useSupabaseUser();
const client = useSupabaseClient();
const router = useRouter();

async function logout() {
  try {
    const { error } = await client.auth.signOut();
    if (error) throw error;
    router.push("/");
  } catch (error) {
      console.log(error.message);
  }
}
</script>


To center the transparent textbox containing the text both horizontally and vertically on the whole page, you can use flexbox for the main container. Here's the modified code:

html
Copy code
<template>
  <main style="display: flex; flex-direction: column; align-items: center; justify-content: center; height: 100vh; background-image: url('https://img.freepik.com/free-vector/worldwide-connection-blue-background-illustration-vector_53876-76826.jpg?w=1380&t=st=1706417840~exp=1706418440~hmac=8f5e49608254d1d0525f522a7aaee378db1e6139bc45cdcd2c849430143d0505'); background-size: cover; background-position: center;">
    <div class="text-container">
      <h1 class="login">LOGIN SUCCESSFUL</h1>
      <h1>You have successfully signed into your account.</h1>
    </div>
    <nav class="navbar">
      <div class="buttons">
        <NuxtLink to="/" class="navbar-link">Home</NuxtLink>
        <NuxtLink to="/employees" class="navbar-link">View Employees</NuxtLink>
        <NuxtLink to="/departments" class="navbar-link">View Departments</NuxtLink> 
        <NuxtLink to="/adddataforms" class="navbar-link">Add Forms</NuxtLink>       
      </div>
      <div class="logout-container">
        <button @click="logout" class="logout-button">Logout</button>
      </div>
    </nav>
  </main>
</template>

<style scoped>

.login {
  font-size: 30px
}
.text-container {
    background: rgba(68, 68, 69, 0.5);
    padding: 50px;
    border-radius: 20px;
    text-align: center
    
  }

  .profile {
    text-align: center;
    margin: 20px;
    font-size: 30px;
 
  }

  h1 {
    color: #06f857;
  }

  .navbar {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    width: auto;
    background: rgba(255, 255, 255, 0.7);
    padding: 8px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    margin: auto;
    display: flex;
    justify-content: space-between; 
    align-items: center; 
  }

  .buttons {
    display: flex;
    align-items: center;
    margin-left: 30px;
  }

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

  .logout-button {
    padding: 5px 30px;
    font-size: 1em;
    color: #333;
    background-color: #fff; 
    border: none;
    border-radius: 20px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }

  .logout-button:hover {
    background-color: #eee;
  }

  .navbar-link {
    margin-right: 5px;
    text-decoration: none;
    color: #333;
    background-color: #eee;
    padding: 5px 10px;
    border-radius: 5px;
    transition: background-color 0.3s ease;
  }
  .navbar-link:hover {
    background-color: #ddd;
  }

</style>
