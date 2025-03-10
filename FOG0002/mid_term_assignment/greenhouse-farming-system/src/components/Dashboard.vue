<script setup>
import { ref, onMounted } from 'vue';
import { useRouter } from 'vue-router';
import Navbar from './Navbar.vue';

const router = useRouter();
const metrics = ref([]);

onMounted(() => {
    const user = localStorage.getItem("user");
    if (!user) {
        router.push({ name: 'Login' });
    }
});

const fetchData = async () => {
  try {
    const response = await fetch('../../DB/data.json'); 
    metrics.value = await response.json();
  } catch (error) {
    console.error('Error fetching data:', error);
  }
};

onMounted(fetchData);

</script>

<template>
  <div id="dashboard">
    <Navbar />

    <main>
      <header>
        <h1>Dashboard</h1>
        <p>Real-time Monitoring of Greenhouse Conditions</p>
      </header>

      <section class="metrics">
        <div 
          v-for="(metric, index) in metrics" 
          :key="index" 
          class="card" 
          :style="{ borderLeft: `5px solid ${metric.color}` }"
        >
          <h2>{{ metric.title }}</h2>
          <p>{{ metric.value }}</p>
        </div>
      </section>
    </main>
  </div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Roboto', sans-serif;
  background: #f4f6f9;
  color: #333;
  padding-top: 70px;
}

main {
  padding: 2rem 3rem;
}

header h1 {
  font-size: 2.5rem;
  font-weight: 700;
  color: #34495e;
  margin-bottom: 10px;
}

header p {
  font-size: 1.1rem;
  color: #7f8c8d;
  font-weight: 300;
}

.metrics {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 30px;
  margin-top: 30px;
}

.card {
  padding: 1.8rem;
  border-radius: 10px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
  text-align: center;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
}


.card h2 {
  font-size: 1.5rem;
  margin-bottom: 10px;
}

.card p {
  font-size: 2rem;
  font-weight: 600;
}

.temperature-card {
  border-left: 5px solid #e74c3c;
}

.humidity-card {
  border-left: 5px solid #16a085;
}

.moisture-card {
  border-left: 5px solid #f39c12;
}

.light-card {
  border-left: 5px solid #3498db;
}

@media (max-width: 1024px) {
  main{
    margin-top: 30%;
  }
  
  .metrics {
    grid-template-columns: repeat(2, 1fr);
  }

  .navbar {
    padding: 1.2rem 1.5rem;
  }

  .nav-links li a {
    font-size: 1rem;
  }
}

@media (max-width: 768px) {
  main{
    margin-top: 30%;
  }
  .metrics {
    grid-template-columns: 1fr;
  }
  .navbar li{
    margin-left: 20px;
  }
  header h1 {
    font-size: 2rem;
  }
  header h1 {
    margin-top: 30px;
  }
  header p {
    font-size: 1rem;
  }

  .card {
    padding: 1.5rem;
  }

  .card h2 {
    font-size: 1.3rem;
  }

  .card p {
    font-size: 1.8rem;
  }
}

@media (max-width: 480px) {
  main{
    margin-top: 30%;
  }

  .navbar {
    flex-direction: column;
    align-items: flex-start;
    padding: 1.2rem;
  }

  .navbar li{
    margin-left: 20px;
  }
  .nav-links {
    display: flex;
    flex-direction: row;
    gap: 10px;
    overflow-x: auto;
    -webkit-overflow-scrolling: touch;
    max-width: 100%;
    white-space: nowrap;
  }

  header h1 {
    margin-top: 30px;
  }

  .nav-links li {
    flex-shrink: 0;
  }

  .logo {
    font-size: 1.6rem;
    margin-bottom: 10px;
  }

  .metrics {
    margin-top: 20px;
  }

  .card {
    padding: 1rem;
  }

  .card-icon {
    font-size: 2rem;
  }

  .card h2 {
    font-size: 1.2rem;
  }

  .card p {
    font-size: 1.5rem;
  }
}
</style>
