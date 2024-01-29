<script setup>
const user = useSupabaseUser();
const client = useSupabaseClient();
const router = useRouter();

async function logout() {
  try {
    const { error } = await client.auth.signOut();
    if (error) throw error;
    router.push("/login");
  } catch (error) {
      console.log(error.message);
  }
}
</script>

<template>
  <main style="background-image: url('https://img.freepik.com/free-vector/worldwide-connection-blue-background-illustration-vector_53876-76826.jpg?w=1380&t=st=1706417840~exp=1706418440~hmac=8f5e49608254d1d0525f522a7aaee378db1e6139bc45cdcd2c849430143d0505'); 
  background-size: cover; background-position: center; height: 100vh;">
    <div class="profile">
      <h1>Profile Page</h1>
    </div>
    <nav class="navbar">
      <div class="buttons">
        <NuxtLink to="/" class="navbar-link">Home</NuxtLink>
        <NuxtLink to="/employees" class="navbar-link">View Employees</NuxtLink>
        <NuxtLink to="/departments" class="navbar-link">View Departments</NuxtLink>     
      </div>
      <!-- Place the logout button on the right side -->
      <div class="logout-container">
        <button @click="logout" class="signup-button">Logout</button>
      </div>
    </nav>
  </main>
</template>

<style scoped>
  /* Add your styling here if needed */
  .profile {
    text-align: center;
    margin: 20px;
  }

  h1 {
    color: #007bff;
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
    justify-content: space-between; /* Use space-between to push items to the ends */
    align-items: center; /* Center items vertically */
  }

  .buttons {
    display: flex;
    align-items: center;
    margin-left: 30px;
  }

  .navbar-link {
    margin-right: 20px;
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

  .signup-button {
    padding: 5px 30px;
    font-size: 1em;
    color: #333;
    background-color: #fff;
    border: none;
    border-radius: 20px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }

  .signup-button:hover {
    background-color: #eee;
  }

  .logout-container {
    margin-right: 30px;
  }
</style>
