<template>
  <main style="background-image: url('https://img.freepik.com/free-vector/worldwide-connection-blue-background-illustration-vector_53876-76826.jpg?w=1380&t=st=1706417840~exp=1706418440~hmac=8f5e49608254d1d0525f522a7aaee378db1e6139bc45cdcd2c849430143d0505'); background-size: cover; background-position: center; height: 100vh;">
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
    <div class="center-container">
      <div class="data-entry-forms">
        <form @submit.prevent="submitPersonalInfoForm">
          <h3 class="personal-info"><strong>Personal Information</strong></h3>
          <label for="firstname">First Name:</label>
          <input type="text" id="firstName" v-model="personalInfo.firstName" required />

          <label for="lastname">Last Name:</label>
          <input type="text" id="lastName" v-model="personalInfo.lastName" required />

          <label for="age">Age:</label>
          <input type="number" id="age" v-model="personalInfo.age" required />

          <label for="email">Email:</label>
          <input type="email" id="email" v-model="contactInfo.email" required />

          <label for="phoneNumber">Phone Number:</label>
          <input type="tel" id="phoneNumber" v-model="contactInfo.phoneNumber" required />

          <button type="submit">Submit</button>
        </form>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  data() {
    return {
      personalInfo: {
        firstName: '',
        lastName: '',
        age: null,
      },
      contactInfo: {
        email: '',
        phoneNumber: '',
      },
      loginCredentials: {
        username: '',
        password: '',
      },
    };
  },
  methods: {
    submitPersonalInfoForm() {
      console.log('Personal Information Form submitted:', this.personalInfo);
      this.resetForm('personalInfo');
    },
    submitContactInfoForm() {
      console.log('Contact Information Form submitted:', this.contactInfo);
      this.resetForm('contactInfo');
    },
    submitLoginCredentialsForm() {
      console.log('Login Credentials Form submitted:', this.loginCredentials);
      this.resetForm('loginCredentials');
    },
    resetForm(formKey) {
      this[formKey] = {};
    },
  },
};
</script>

<style scoped>

.personal-info {
  color: rgb(4, 179, 161);
  font-size: 25px;
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
.data-entry-forms {
  max-width: 400px;
  margin: 80px auto;
  color: white;
  width: 100%;
}

.center-container {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}

h2, h3 {
  text-align: center;
}

form {
  margin-bottom: 20px;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 10px;
}

label {
  display: block;
  margin-top: 10px;
}

input {
  width: 100%;
  padding: 8px;
  margin-top: 5px;
  box-sizing: border-box;
  color: black;
}

button {
  background-color: #007bff;
  color: #fff;
  padding: 5px 10px;
  cursor: pointer;
  border: none;
  display: block;
  margin: 0 auto;

}
</style>