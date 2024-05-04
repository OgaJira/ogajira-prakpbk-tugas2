<template>
  <div class="login-container">
    <h1><b>WEB.AKOH</b></h1>
    <h2><b>Masuk</b></h2>

    <form @submit.prevent="login" class="login-form">
      <div class="form-group">
        <label for="username">Username</label>
        <input type="text" id="username" v-model="username" :class="{ 'error': usernameError }" placeholder="Masukkan Username">
        <span v-if="usernameError" class="error-message">Username tidak boleh kosong</span>
      </div>

      <div class="form-group">
        <label for="password">Password</label>
        <input type="password" id="password" v-model="password" :class="{ 'error': passwordError }" placeholder="Masukkan Password">
        <span v-if="passwordError" class="error-message">Password tidak boleh kosong</span>
      </div>

      <button type="submit" :style="{ backgroundColor: buttonColor }">Masuk</button>
      <a href="#" @click="forgotPassword" :style="{ color: linkColor, textDecoration: linkDecoration }">Lupa Password?</a> <!-- Tautan lupa password dengan style bindings -->
    </form>

    <!-- Interaksi dinamis dengan event listener -->
    <button @click="changeText" :style="{ backgroundColor: buttonColor, color: buttonTextColor }">Daftar</button> <!-- Tombol dengan style bindings -->
    
    <!-- Pesan untuk login berhasil -->
    <div v-if="loginSuccess" class="success-message">Login berhasil!</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: '',
      password: '',
      usernameError: false,
      passwordError: false,
      linkColor: '#007bff', // Warna default untuk tautan lupa password
      linkDecoration: 'none', // Dekorasi default untuk tautan lupa password
      buttonColor: '#007bff', // Warna default untuk tombol
      buttonTextColor: '#fff', // Warna teks default untuk tombol
      loginSuccess: false // Untuk menampilkan pesan login berhasil
    };
  },
  methods: {
    login() {
      // Validasi input sebelum login
      this.usernameError = !this.username.trim();
      this.passwordError = !this.password.trim();

      // Jika kedua input valid, lakukan proses login
      if (!this.usernameError && !this.passwordError) {
        // Lakukan proses login sesuai kebutuhan, misalnya dengan menggunakan axios atau fetch
        // Di sini saya asumsikan login berhasil, Anda dapat menyesuaikan sesuai kebutuhan
        this.loginSuccess = true;

        // Redirect ke halaman berikutnya setelah login berhasil
        setTimeout(() => {
          this.$router.push('/halaman-berikutnya');
        }, 2000); // Redirect setelah 2 detik
      }
    },
    changeText() {
      // Fungsi untuk mengubah teks
      // Anda dapat menambahkan logika sesuai kebutuhan Anda di sini
    },
    forgotPassword() {
      // Logika untuk pemulihan password
      // Anda dapat mengarahkan pengguna ke halaman pemulihan password di sini
      console.log('Pergi ke halaman pemulihan password...');
    }
  }
};
</script>

<style scoped>
.login-container {
  max-width: 400px;
  margin: 50px auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #fff;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
  text-align: center; /* Memastikan konten berada di tengah */
}

.login-form {
  display: flex;
  flex-direction: column;
}

.form-group {
  margin-bottom: 15px;
}

label {
  font-weight: bold;
}

input[type="text"],
input[type="password"],
button {
  width: 100%; /* Lebar input dan tombol 100% */
  padding: 10px;
  margin-bottom: 10px; /* Spasi bawah */
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}

button {
  cursor: pointer;
  color: #fff; /* Warna teks tombol */
}

button:hover {
  background-color: #0056b3;
}

.error-message {
  color: red;
}

.success-message {
  color: green;
}
</style>
