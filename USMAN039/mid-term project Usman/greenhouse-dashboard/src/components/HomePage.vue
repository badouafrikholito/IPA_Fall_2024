<script setup>
import { useRouter } from 'vue-router';
const router = useRouter();

const afterLogin = () => {
  const user = localStorage.getItem("user");
  if (user) {
    router.push({ name: 'Dashboard' });
  }
};
</script>

<template>
  <div id="home-page">
    <div class="home-content">
      <header class="header">
        <h1 class="title">Greenhouse Farming System</h1>
        <p class="subtitle"> sustainable agriculture with technology</p>
      </header>

      <section class="info-section">
        <p>Welcome to the Greenhouse Farming System,  Explore the features:</p>
      </section>

      <div class="buttons">
        <router-link to="/login" @click="afterLogin" class="button login-button">Login</router-link>
        <router-link to="/signup" @click="afterLogin" class="button signup-button">Signup</router-link>
      </div>
    </div>
  </div>
</template>

<style scoped>

:root {
  --primary-color: #3498db;
  --secondary-color: #2ecc71;
  --accent-color: #f39c12;
  --background-color: #ffffff;
  --text-color: #333333;
  --light-text-color: #7f8c8d;
  --button-hover-color: rgba(0, 0, 0, 0.2);
  --shadow-color: #3eaa00e7;
}
#home-page {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
  position: relative;
  overflow: hidden;
}
.home-content {
  text-align: center;
  background: var(--background-color);
  padding: 40px;
  border-radius: 20px;
  box-shadow: 0 15px 30px var(--shadow-color);
  max-width: 600px;
  width: 100%;
  position: relative;
  z-index: 1;
  margin: 0 20px;
}
.header {
  margin-bottom: 30px;
}

.title {
  font-size: 2.5rem;
  color: var(--text-color);
  font-weight: 700;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
}

.subtitle {
  font-size: 1.1rem;
  color: var(--light-text-color);
  margin-top: 10px;
}
.info-section {
  font-size: 1rem;
  color: var(--text-color);
  line-height: 1.6;
  margin: 20px 0;
}
.features-list {
  list-style-type: none;
  padding: 0;
  margin: 15px 0;
  font-size: 1.1rem;
}

.features-list li {
  background: #ecf8e1;
  padding: 12px;
  border-radius: 8px;
  margin-bottom: 12px;
  font-weight: 500;
}

.features-list li:nth-child(odd) {
  background: #d1f1e1;
}
.buttons {
  display: flex;
  gap: 25px;
  justify-content: center;
  margin-top: 30px;
}

.button {
  padding: 14px 30px;
  font-size: 1.1rem;
  font-weight: 600;
  color: wheat;
  border: whitesmoke;
  cursor: pointer;
  border-radius: 10px;
  transition: all 0.3s ease;
  text-decoration: none;
  box-shadow: 0px 8px 20px var(--shadow-color);
}

.button:hover {
  background: linear-gradient(90deg, #c90000, #ff5b5b);
}

.login-button {
  background-color: #e75714;
}

.signup-button {
  background-color: #f40e0e;
}

.login-button:hover {
    background: linear-gradient(90deg, #c90000, #ff5b5b);
}

.signup-button:hover {
    background: linear-gradient(90deg, #c90000, #ff5b5b);
}
@media (max-width: 768px) {
  .home-content {
    padding: 30px;
    max-width: 90%;
  }

  .title {
    font-size: 2rem;
  }

  .subtitle {
    font-size: 1rem;
  }

  .features-list li {
    font-size: 1rem;
  }

  .button {
    padding: 12px 26px;
  }
}

@media (max-width: 480px) {
  .title {
    font-size: 1.8rem;
  }

  .subtitle {
    font-size: 0.9rem;
  }

  .features-list li {
    font-size: 0.95rem;
  }

  .buttons {
    flex-direction: column;
    gap: 20px;
  }
}

</style>