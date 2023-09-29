<script setup>
  import { ref } from 'vue';
  import '@/assets/style.css';

  const username = ref('');
  const password = ref('');
  const isRegistered = ref(false);
  const registrationError = ref(false);
  
  function register() {
  // Check if the username already exists in localStorage
  const registeredUsername = localStorage.getItem('registeredUsername');
  if (registeredUsername === username.value) {
    registrationError.value = true; 
    } else {
      // Store the new registration data
      localStorage.setItem('registeredUsername', username.value);
      localStorage.setItem('registeredPassword', password.value);

      isRegistered.value = true; 
      registrationError.value = false; 
    }
  }
</script>

<style scoped>
    input,
    label,
    button {
        display: flex;
        justify-content: center;
        margin: auto !important;
        float: center;
        width: 250px;
    }

</style>

<template>
    <div>
      <h1>Registration Page</h1>
      <form @submit.prevent="register">
        <label for="username">USERNAME:</label>
        <input type="text" id="username" v-model="username" required />
        <br />
  
        <label for="password">PASSWORD:</label>
        <input type="password" id="password" v-model="password" required />
        <br />
  
        <button type="submit">Register</button>
      </form>
  
      <p v-if="isRegistered">Registration successful! Welcome: {{ registeredUsername }}.</p>
      <p v-if="registrationError">Username already exists. Please choose a different one.</p>

    </div>
  </template>
  
  
  