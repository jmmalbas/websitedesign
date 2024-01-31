<script setup>
const { data } = await useFetch("/api/departments", {
  headers: useRequestHeaders(["cookie"]),
});
let departments = data._value.departments;

const sortedDepartments = departments.slice().sort((a, b) => a.DEPARTMENT_NAME.localeCompare(b.DEPARTMENT_NAME));

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
  <main style="background-image: url('https://lh3.googleusercontent.com/pw/ABLVV861lwJ6BLppPj58uHfLnDEI1_U932rgRCX4azyTBSNsCU6vdJ4wsuhUgFYzeDLI89mvIPV5lQu4Q0NVjSIva4kn-0676P1iQLLDuqOzaO-2eycNozdqRpr8QbufNkYeg4ZLKPdC5PV6rFQIPGpjTBj-BL33pO7qlATLEJ3-0YPpWH7ehIxjR9QmpafAFOOy7pft3mvrZEU-ONcI4DVqIDBCFLLMN-moLZOza6v5wtpPYsRIsCfJMbsN0CGeKQAvR1oIprpm3f9zFug4Ln2X6J8uyB0ljSg2p6Pwe8v_3JgCx9Xbl49OY31g-jt4P6JYwj1n1UswC4G7tIyegk1lEXnK1hzUn2AUGFWcBdBR6oyFvdT4k9dfA7VCoAStOavnvlJ18ClZQ7P8dwP3yMOvzn56vdAjIsaaxAaFi95-c7YpgQqAJCC6j5HHOAofd_wgUBnhoK3Gr7_4zBrfeyCrg6cRaCMqUunJPWZz9OC4jYrnW7oP70hqtA6mvK89RqkyWPd0pw5pyzAP13c6ZiTKqBiFLg2qsPnxRu_ybb817rI-j1dVpNR7uNwylGraBdtv_xQ3EEkMsfHul5N8sMFdvdfNQPhoDq5WR7iDZaRxkUPZNjP4GUm1mWq_VQxLlOZZhEzoYQ5ikgwpmCfSmCxb-70NfFRX81LgkwsoWVfFcbVTWk7mjPqEVvV7HTT0lA-NLfMhqcikyHG0pjQzNJR4d9sdLPq_OorXGpgRg15siIpz_ueF1h_1eRXTK2ty6oKbMrZYDpR5fsOQWs7wPWxyKAN_ZXhhyTcAwFlWlBasGVyciN-xx_4mB6O6RgsdH89V6HOfBl9l1WcUE75oUPfzk4f-tQF00GDVZo50fwwIY2pFMCKxuThiWPorDvbAPKgt4lPLY3k4NRChNxp0ToKk6sS0=w1380-h862-s-no-gm?authuser=0'); 
    background-size: cover; background-position: center; height: 100vh;">
    <div class="departments-container">
      <h1 class="dept"><strong>Departments</strong></h1>
  
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
  max-width: 1500px; 
}


.department-container {
  background-color: rgba(0, 0, 0, 0.5);
  padding: 20px; 
  border-radius: 10px; 
}

.department-columns {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 10px; 
}

.department-item {
  padding: 10px;
  border: 1px solid #ccc;
  color: rgb(183, 182, 182); 
  transition: transform 0.3s ease; 
}

.department-item:hover {
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

.dept {
  color: white;
    font-size: 4em;
    padding: 40px;
    margin: auto 0;
    transition: color 0.3s ease;
  }

  .emp:hover {
    color: red;
  }

.dept {
    color: white;
    font-size: 4em;
    padding: 40px;
    margin: auto 0; 
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

