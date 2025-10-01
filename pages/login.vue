<template>
  <div class="auth-container">
    <h1>Login in system</h1>
    <form @submit.prevent="handleSubmit">
      <div class="input-group">
        <label>Login:</label>
        <input 
          v-model="login" 
          type="text" 
          placeholder="Type your login"
          required
        >
      </div>
      <div class="input-group">
        <label>Password:</label>
        <input 
          v-model="password" 
          type="password" 
          placeholder="Type your password"
          required
        >
      </div>
      <button type="submit">Sign In</button>
    </form>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const login = ref('');
const password = ref('');

const handleSubmit = () => {
  console.log('Отправка данных:', {
    login: login.value,
    password: password.value
  });
  // Здесь будет ваша логика авторизации
};
</script>

<style scoped>
.auth-container {
  max-width: 300px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 5px;
  margin-top: 50px;
}

h1 {
  text-align: center;
  margin-bottom: 20px;
}

.input-group {
  margin-bottom: 15px;
}

label {
  display: block;
  margin-bottom: 5px;
}

input {
  width: 100%;
  padding: 8px;
  box-sizing: border-box;
  border: 1px solid #ccc;
  border-radius: 3px;
}

button {
  width: 100%;
  padding: 10px;
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 3px;
  cursor: pointer;
}

button:hover {
  background-color: #369f6b;
}
</style>