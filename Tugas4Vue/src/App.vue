<template>
  <div id="app">
    <!-- Click Counter -->
    <section class="section">
      <h2 class="title">Click Counter</h2>
      <button class="btn" @click="count++">Klik Saya: {{ count }}</button>
    </section>

    <!-- Box Color Changer -->
    <section class="section">
      <h2 class="title">Box Color Changer</h2>
      <div class="box" :style="{ backgroundColor: boxColor }"></div>
      <button class="btn" @click="changeBoxColor">Ganti Warna Box</button>
    </section>

    <!-- Image Carousel -->
    <section class="section">
      <h2 class="title">Image Carousel</h2>
      <div class="carousel">
        <img :src="images[currentImage]" alt="Image Carousel">
      </div>
      <div class="carousel-controls">
        <button class="btn small" @click="prevImage">Sebelumnya</button>
        <button class="btn small" @click="nextImage">Selanjutnya</button>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      count: 0, // Counter
      boxColors: ['#74c0fc', '#ffa94d', '#94d82d', '#f783ac', '#f06595'], // Warna yang menarik
      boxColorIndex: 0,
      images: [
        'https://via.placeholder.com/400x300.png?text=Image+1',
        'https://via.placeholder.com/400x300.png?text=Image+2',
        'https://via.placeholder.com/400x300.png?text=Image+3'
      ],
      currentImage: 0
    };
  },
  computed: {
    boxColor() {
      return this.boxColors[this.boxColorIndex];
    }
  },
  methods: {
    changeBoxColor() {
      this.boxColorIndex = (this.boxColorIndex + 1) % this.boxColors.length;
    },
    prevImage() {
      this.currentImage =
        (this.currentImage - 1 + this.images.length) % this.images.length;
    },
    nextImage() {
      this.currentImage = (this.currentImage + 1) % this.images.length;
    }
  }
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap');

/* Styling utama */
body {
  font-family: 'Poppins', sans-serif;
  background-color: #f4f7fb;
  margin: 0;
  padding: 0;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

#app {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  gap: 40px; /* Berikan jarak antar elemen */
}

/* Section styling */
.section {
  margin-bottom: 60px; /* Jarak vertikal antar section */
}

/* Title section */
.title {
  font-size: 1.5em;
  margin-bottom: 20px;
  color: #333;
}

/* Tombol dengan transisi */
.btn {
  background-color: #3498db;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-size: 14px;
  transition: background-color 0.3s ease, transform 0.2s ease;
}

.btn:hover {
  background-color: #2980b9;
  transform: scale(1.05);
}

.btn.small {
  padding: 8px 12px;
  margin: 5px;
}

/* Kotak warna */
.box {
  width: 120px;
  height: 120px;
  margin: 20px auto;
  border-radius: 10px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
}

/* Carousel styling */
.carousel img {
  width: 400px;
  border-radius: 10px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
}

/* Kontrol carousel */
.carousel-controls {
  margin-top: 15px;
}
</style>
