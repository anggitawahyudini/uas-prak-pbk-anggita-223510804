<template>
  <!-- Tambahkan di bagian head atau sebelum bagian template -->
  <q-header elevated class="navbar">
    <q-toolbar>
      <q-toolbar-title class="title">Cuaca🌞</q-toolbar-title>

      <!-- Tombol untuk Tugas 1 -->
      <q-btn
        label="Tugas 1📝"
        @click="navigateToTask('https://contoh-iota.vercel.app/')"
        class="task-btn"
      />

      <!-- Tombol untuk Tugas 2 -->
      <q-btn
        label="Tugas 2📅"
        @click="navigateToTask('https://anggitatugas2.netlify.app')"
        class="task-btn"
      />

      <!-- Tombol untuk Tugas 3 -->
      <q-btn
        label="Tugas 3📋"
        @click="navigateToTask('https://anggita-tugas3.vercel.app/')"
        class="task-btn"
      />

      <!-- Tombol untuk Tugas 4 -->
      <q-btn
        label="Tugas 4📅"
        @click="navigateToTask('https://anggitawahyudinip-tugas4.vercel.app/')"
        class="task-btn"
      />

      <!-- Tombol untuk Tugas 5 -->
      <q-btn
        label="Tugas 5📋"
        @click="navigateToTask('https://anggita-tugas5.vercel.app/')"
        class="task-btn"
      />

      <!-- Tombol untuk Tugas 6 -->
      <q-btn
        label="Tugas 6📅"
        @click="navigateToTask('https://main--tugas6-gita.netlify.app/')"
        class="task-btn"
      />
    </q-toolbar>
  </q-header>
</template>

<script>
export default {
  name: 'Navbar',
  methods: {
    navigateToTask(url) {
      window.open(url, '_blank'); // Buka tautan di tab atau jendela baru
    }
  }
};
</script>

<style scoped>
.navbar {
  background: linear-gradient(45deg, #ff9a9e, #fecfef);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.title {
  font-family: 'Pacifico', cursive;
  font-size: 24px;
  color: #fff;
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.1);
}

.task-btn {
  margin-right: 12px;
  background-color: linear-gradient(45deg, #f908d5, #d85fb2);
  color: #f0f4f9;
  font-weight: bold;
  border-radius: 20px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  transition: transform 0.3s, background-color 0.3s, box-shadow 0.3s;
}

.task-btn:hover {
  background-color: #ff8a8a;
  transform: scale(1.05);
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.2);
}

.task-btn:active {
  background-color: #ff7b7b;
  transform: scale(1);
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}

/* Tambahkan padding pada q-toolbar untuk memberikan sedikit ruang di sekitar elemen */
.q-toolbar {
  padding: 10px;
}

/* Pastikan tombol memiliki ukuran yang sesuai di perangkat kecil */
@media (max-width: 600px) {
  .task-btn {
    font-size: 14px;
    margin-right: 8px;
    padding: 6px 12px;
  }

  .title {
    font-size: 18px;
  }
}
</style>
