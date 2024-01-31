<script setup>
  const { data } = await useFetch("/api/employees", {
    headers: useRequestHeaders(["cookie"]),
  });
  let employees = data._value.employees;

 
  const sortedEmployees = employees.slice().sort((a, b) => a.FIRST_NAME.localeCompare(b.FIRST_NAME));

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

<template>
  <main style="background-image: url('https://img.freepik.com/free-vector/worldwide-connection-blue-background-illustration-vector_53876-76826.jpg?w=1380&t=st=1706417840~exp=1706418440~hmac=8f5e49608254d1d0525f522a7aaee378db1e6139bc45cdcd2c849430143d0505'); 
  background-size: cover; background-position: center; height: 100vh;">
    <div class="employees-container">
      <h1 class="emp"><strong>Employees</strong></h1>
      
      <div class="employee-container">
        <div class="employee-columns">
          <div v-for="employee in sortedEmployees" :key="employee.EMPLOYEE_ID" class="employee-item">
            {{ employee.FIRST_NAME }} {{ employee.LAST_NAME }}
          </div>
        </div>
      </div>
    </div>
    <nav class="navbar">
      <div class="buttons">
        <NuxtLink to="/" class="navbar-link">Home</NuxtLink>
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
  .employees-container {
    text-align: center;
    margin: auto;
    max-width: 1500px; 
  }

  .employee-container {
    background-color: rgba(0, 0, 0, 0.5); 
    padding: 20px; 
    border-radius: 10px; 
  }

  .employee-columns {
    display: grid;
    grid-template-columns: repeat(8, 3fr);
    gap: 5px; 
  }

  .employee-item {
    padding: 10px;
    border: 1px solid #ccc;
    color: rgb(183, 182, 182); 
    transition: transform 0.3s ease; 
  }

  .employee-item:hover {
    transform: scale(1.1); 
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
    margin-left: 10px;
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

  .emp {
    color: white;
    font-size: 4em;
    padding: 40px;
    margin: auto 0; 
    transition: color 0.3s ease;
  }

  .emp:hover {
    color: red;
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