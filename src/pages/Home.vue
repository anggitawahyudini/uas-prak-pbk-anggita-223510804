<template>
  <div class="container">
    <div class="weather-widget">
      <input v-model="location" placeholder="Masukkan lokasi🌍" @keyup.enter="getWeather" />
      <button @click="getWeather">🌤️Cari Cuaca🌦️</button>

      <div v-if="isLoading" class="loading">
        <img src="https://cdn-icons-png.flaticon.com/512/1496/1496760.png" alt="Loading Icon" />
        <p>Memuat data...</p>
      </div>

      <div v-if="weather && !isLoading" class="weather-info">
        <div class="weather-header">
          <img :src="`http://openweathermap.org/img/wn/${weather.weather[0].icon}@2x.png`" alt="Weather Icon" />
          <h2>{{ location }}</h2>
        </div>
        <p class="temperature">{{ weather.main.temp }} °C</p>
        <p class="description">{{ weather.weather[0].description }}</p>
        <p>Kelembaban: {{ weather.main.humidity }} %</p>
        <p>Kecepatan Angin: {{ weather.wind.speed }} m/s</p>
      </div>

      <div v-if="error && !isLoading" class="error">{{ error }}</div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      apiKey: '82e5c1fda627ad908e153efc9104469d',
      location: '',
      weather: null,
      error: null,
      isLoading: false,
    };
  },
  methods: {
    async getWeather() {
      this.isLoading = true;
      const apiUrl = `https://api.openweathermap.org/data/2.5/weather?q=${this.location}&units=metric&lang=id&appid=${this.apiKey}`;
      try {
        const response = await axios.get(apiUrl);
        setTimeout(() => {
          this.weather = response.data;
          this.error = null;
          this.isLoading = false;
        }, 1000); // 
      } catch (err) {
        setTimeout(() => {
          this.weather = null;
          this.error = 'Tidak dapat mengambil data cuaca. Silakan coba lagi.';
          this.isLoading = false;
        }, 1000); // 
      }
    }
  }
};
</script>

<style scoped>
.weather-widget {
  max-width: 350px;
  margin: 0 auto;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
  font-family: 'Helvetica Neue', Arial, sans-serif;
  background: linear-gradient(to top right, #d3bb5a 0%, #f9a4ff 100%);
  color: #fff;
  text-align: center;
}

.weather-widget input {
  width: calc(100% - 22px);
  padding: 10px;
  margin-bottom: 15px;
  border: none;
  border-radius: 5px;
  outline: none;
}

.weather-widget button {
  width: 100%;
  padding: 10px;
  background-color: #ff5f6d;
  background-image: linear-gradient(to right, #ff5f6d, #ffc371);
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-weight: bold;
}

.weather-widget button:hover {
  background-image: linear-gradient(to right, #ffc371, #ff5f6d);
}

.weather-info {
  margin-top: 20px;
}

.weather-header {
  display: flex;
  align-items: center;
  justify-content: center;
}

.weather-header img {
  width: 50px;
  height: 50px;
}

.weather-header h2 {
  margin-left: 10px;
  font-size: 24px;
}

.temperature {
  font-size: 48px;
  margin: 10px 0;
}

.description {
  font-style: italic;
}

.weather-info p {
  margin: 5px 0;
}

.error {
  color: #ff5f6d;
  margin-top: 10px;
  font-weight: bold;
}

.container {
  position: relative;
  min-height: 50vh;
  margin-top: 50px;
}

.loading {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 20px;
}

.loading img {
  width: 50px;
  height: 50px;
}

.loading p {
  margin-top: 10px;
  font-size: 18px;
  color: #fff;
}
</style>
