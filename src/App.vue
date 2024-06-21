<template>
  <q-layout view="hHh lpR fFf">
    <q-page-container>
      <router-view />
    </q-page-container>

    <!-- Menggunakan komponen Navbar -->
    <Navbar @task-change="handleTaskChange" />

    <q-page padding>
      <WeatherWidget v-if="selectedTask === 'task1'" />
      <!-- Tambahkan kondisi lain untuk tugas lainnya -->
    </q-page>

    <!-- Menggunakan komponen Footer -->
    <Footer />
  </q-layout>
</template>

<script>
import Navbar from './components/Navbar.vue'; // Sesuaikan path sesuai struktur proyek Anda
import Footer from './components/Footer.vue'; // Sesuaikan path sesuai struktur proyek Anda

export default {
  name: 'App',

  components: {
    Navbar,
    Footer
  },

  data() {
    return {
      selectedTask: null
    };
  },

  methods: {
    handleTaskChange(task) {
      this.selectedTask = task;
    }
  }
};
</script>

<style>
/* Tambahkan gaya CSS sesuai kebutuhan aplikasi Anda */
</style>
