<template>
  <main style="background-image: url('https://img.freepik.com/free-vector/worldwide-connection-blue-background-illustration-vector_53876-76826.jpg?w=1380&t=st=1706417840~exp=1706418440~hmac=8f5e49608254d1d0525f522a7aaee378db1e6139bc45cdcd2c849430143d0505'); 
    background-size: cover; background-position: center; height: 100vh;">
    <div class="departments-container">
      <h1 class="dept"><strong>Departments</strong></h1>
      <!-- Create a container for the department columns with a transparent background -->
      <div class="department-container">
        <div class="department-columns">
          <div v-for="department in sortedDepartments" :key="department.DEPARTMENT_ID" class="department-item">
            {{ department.DEPARTMENT_NAME }}
          </div>
        </div>
      </div>
    </div>
    <nav class="navbar">
      <div class="buttons">
        <NuxtLink to="/" class="navbar-link">Home</NuxtLink>
        <NuxtLink to="/employees" class="navbar-link">View Employees</NuxtLink>
        <NuxtLink to="/adddataforms" class="navbar-link">Add Forms</NuxtLink> 
      </div>
      <div class="logout-container">
        <button @click="logout" class="logout-button">Logout</button>
      </div>
    </nav>
  </main>
</template>

<style scoped>

.departments-container {
  text-align: center;
  margin: auto;
  max-width: 1500px; /* Adjust the max-width as needed */
}

/* Container for department columns with a transparent background */
.department-container {
  background-color: rgba(0, 0, 0, 0.5); /* Transparent black background */
  padding: 20px; /* Adjust the padding as needed */
  border-radius: 10px; /* Add border-radius for rounded corners */
}

.department-columns {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 10px; /* Adjust the gap as needed */
}

.department-item {
  padding: 10px;
  border: 1px solid #ccc;
  color: rgb(183, 182, 182); /* Set white font color */
  transition: transform 0.3s ease; /* Add transition for a smooth effect */
}

.department-item:hover {
  transform: scale(1.1); /* Apply zoom effect on hover */
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
    justify-content: space-between; /* Use space-between to push items to the ends */
    align-items: center; /* Center items vertically */
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
    background-color: #fff; /* White background color */
    border: none;
    border-radius: 20px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }

.signup-button {
  padding: 5px 30px;
  font-size: 1em;
  color: #333;
  background-color: #fff; /* White background color */
  border: none;
  border-radius: 20px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.logout-button {
    padding: 5px 30px;
    font-size: 1em;
    color: #333;
    background-color: #fff; /* White background color */
    border: none;
    border-radius: 20px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }

.logout-button:hover {
  background-color: #eee; /* Light gray background color on hover */
}

.dept {
  color: white;
    font-size: 4em;
    padding: 40px;
    margin: auto 0; /* Add margin to the bottom */
    transition: color 0.3s ease;
  }

  .emp:hover {
    color: red;
  }

.dept {
    color: white;
    font-size: 4em;
    padding: 40px;
    margin: auto 0; /* Add margin to the bottom */
    transition: color 0.3s ease;
  }

  .dept:hover {
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

<script setup>
const { data } = await useFetch("/api/departments", {
  headers: useRequestHeaders(["cookie"]),
});
let departments = data._value.departments;

// Sort the departments alphabetically
const sortedDepartments = departments.slice().sort((a, b) => a.DEPARTMENT_NAME.localeCompare(b.DEPARTMENT_NAME));

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
