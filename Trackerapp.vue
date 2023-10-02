<template>
    <div>
      <header>
        <h1>Clean & Replace Tracker</h1>
        <button @click="logout" v-if="loggedIn">Logout</button>
      </header>
  
      <main>
        <div v-if="loggedIn">
          <!-- Display user dashboard or other content for logged-in users -->
          <h2>Welcome, {{ username }}!</h2>
          <router-link to="/dashboard">Go to Dashboard</router-link>
        </div>
  
        <div v-else>
          <!-- Display login form for users who are not logged in -->
          <h2>Login</h2>
          <form @submit.prevent="login">
            <label for="username">Username:</label>
            <input type="text" id="username" v-model="loginData.username" required>
  
            <label for="password">Password:</label>
            <input type="password" id="password" v-model="loginData.password" required>
  
            <button type="submit">Login</button>
          </form>
        </div>
      </main>
  
      <footer>
        <p>&copy; 2023 Clean & Replace Tracker</p>
      </footer>
    </div>
  </template>
  
  <script>
  export default {
    name: "TrackerApp",
    data() {
      return {
        loggedIn: false,
        username: "",
        loginData: {
          username: "",
          password: "",
        },
      };
    },
    methods: {
      login() {
        // Replace this with your actual login logic using a back-end server and authentication.
        // For demonstration purposes, we'll simulate a successful login with a predefined username and password.
  
        if (this.loginData.username === "user" && this.loginData.password === "password") {
          this.loggedIn = true;
          this.username = this.loginData.username;
        } else {
          alert("Invalid credentials. Please try again.");
        }
      },
      logout() {
        // Implement your logout logic here.
        // Set loggedIn to false and clear user data.
        this.loggedIn = false;
        this.username = "";
      },
    },
  };
  </script>
  
  <style>
  /* Global styles */
  body {
    font-family: Arial, sans-serif;
    background-color: #f0f8ea; /* Light green background */
    margin: 0;
    padding: 0;
  }
  
  h1, h2 {
    color: #000; /* Black text color */
  }
  
  header {
    background-color: #333; /* Dark background color for the header */
    color: #fff; /* White text color for the header */
    padding: 10px;
    text-align: center;
  }
  
  header h1 {
    margin: 0;
    font-size: 24px;
  }
  
  main {
    padding: 20px;
  }
  
  /* Login form styles */
  form {
    background-color: #fff; /* White background for the form */
    padding: 20px;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1); /* Drop shadow effect */
  }
  
  label {
    display: block;
    margin-bottom: 5px;
    color: #333; /* Dark text color */
  }
  
  input[type="text"],
  input[type="password"] {
    width: 100%;
    padding: 10px;
    margin-bottom: 15px;
    border: 1px solid #ccc;
    border-radius: 3px;
    font-size: 16px;
  }
  
  button[type="submit"] {
    background-color: #333; /* Dark background for the button */
    color: #fff; /* White text color for the button */
    padding: 10px 20px;
    border: none;
    border-radius: 3px;
    cursor: pointer;
    font-size: 16px;
  }
  
  button[type="submit"]:hover {
    background-color: #444; /* Darker background on hover */
  }
  
  /* Footer styles */
  footer {
    background-color: #333; /* Dark background color for the footer */
    color: #fff; /* White text color for the footer */
    text-align: center;
    padding: 10px;
  }
  </style>
  
  