<template>
  <div class="harmeilia">
    <h1><i>LOGIN</i></h1>
    <p>Nama:</p>
    <!-- Input nama -->
    <input type="text" v-model="nama" :style="{ 'background-color': buttonBackgroundColor }" @blur="validatenama">
    <p class="input-info">Panjang mak teks 10 karakter </p>
    <p v-if="isRednama" class="red-text">nama tidak valid!</p>
    <p>tampilkan <span :class="{ 'red-text': isRednama }">{{ nama }}</span></p>

    <p>Password:</p>
    <!-- Input password -->
    <input type="password" v-model="password" :style="{ 'background-color': buttonBackgroundColor }" @blur="validatePassword">
    <p class="input-info">Panjang mak teks 10 karakter </p>
    <p v-if="isRedPassword" class="red-text">Password harus memiliki setidaknya 8 karakter (huruf, angka, dan simbol!)</p>
    <p>tampilkan <span :class="{ 'red-text': isRedPassword }">{{ password }}</span></p>

    <!-- Tambahkan input untuk tanggal lahir  -->
    <p>Tanggal Lahir:</p>
    <input type="date" v-model="tanggalLahir">
    
    <!-- V-calendar -->
    <v-calendar v-model="selectedDate"></v-calendar>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nama: '',
      password: '',
      isRednama: false,
      isRedPassword: false,
      buttonBackgroundColor: '#8e12a4',
      selectedDate: null,
      tanggalLahir: '',
    }
  },
  methods: {
    validatenama() {
      // Regular expression for nama validation
      const namaRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      this.isRednama = !namaRegex.test(this.nama);
    },
    validatePassword() {
      // Password validation logic (example: minimum length of 6 characters and at least one number)
      this.isRedPassword = this.password.length < 6 || !/\d/.test(this.password);
    },
  }
}
</script>

<style scoped>
/* CSS Styles */
.harmeilia {
  background: linear-gradient(135deg, #bf21dbde, #e786f9de, #e67ff9de, #c42bdfde, #cc2ce8de);
  background-repeat: no-repeat;
  background-size: cover;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

h1 {
  color: #333;
  height: 10%;
}

p {
  color: #555;
  margin-bottom: 5px;
  text-align: left;
}

input[type="text"], input[type="date"], input[type="password"] {
  width: 20%;
  padding: 10px;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  font-size: 16px;
  box-sizing: border-box;
  z-index: 2; 
}

.input-info {
  font-size: 14px;
  color: #999;
  margin-top: -10px;
  margin-bottom: 10px;
}

span {
  font-size: 18px;
  color: #333;
  font-weight: bold;
}

.red-text {
  color: purple;
}

button {
  padding: 5px 5px;
  background-color: #bf21dbde;
  color: #fff;
  border: none;
  border-radius: 2px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #cc93d6;
}
</style>
