<template>
  <div class="account-page">
    <div class="account-card">
      <h1>My account</h1>
      
      <div class="user-info">
        <div class="avatar">
          <i class="fas fa-user-circle"></i>
        </div>
        <h2>{{ userName }}</h2>
        <p>{{ userEmail }}</p>
      </div>

      <div class="account-actions">
        <button @click="logout" class="logout-btn">
          <i class="fas fa-sign-out-alt"></i> Log Out
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';


const logout = () => {
  router.push('/login');
};
</script>

<style scoped>
.account-page {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 500px;
  background: rgba(0, 0, 0, 0); /* Полупрозрачный фон страницы */
}

.account-card {
  background: rgba(255, 255, 255, 0.9); /* Полупрозрачный белый фон */
  backdrop-filter: blur(5px); /* Эффект размытия */
  border: 1px solid rgba(255, 255, 255, 0.2); /* Едва заметная граница */
  border-radius: 15px;
  padding: 30px;
  width: 100%;
  max-width: 400px;
  text-align: center;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
}

h1 {
  color: #333;
  margin-bottom: 30px;
  font-weight: 600;
}

.user-info {
  margin-bottom: 30px;
}

.avatar {
  font-size: 70px;
  color: rgba(66, 185, 131, 0.8); /* Полупрозрачный цвет */
  margin-bottom: 20px;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

h2 {
  margin: 15px 0;
  color: #333;
  font-size: 1.5rem;
}

p {
  color: #666;
  margin: 5px 0;
  font-size: 1rem;
}

.logout-btn {
  background: rgba(54, 159, 107, 1); /* Полупрозрачный красный */
  color: white;
  border: none;
  padding: 12px 20px;
  border-radius: 8px;
  cursor: pointer;
  font-size: 16px;
  transition: all 0.3s;
  width: 100%;
  margin-top: 20px;
  box-shadow: 0 2px 8px rgba(255, 68, 68, 0.3);
}

.logout-btn:hover {
  background: rgba(204, 0, 0, 0.9); /* Полупрозрачный при наведении */
  transform: translateY(-2px);
}

.fa-sign-out-alt {
  margin-right: 10px;
}
</style>