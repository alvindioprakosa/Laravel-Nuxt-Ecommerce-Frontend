<template>
  <div>
    <!-- Header -->
    <Header />

    <!-- Content -->
    <main class="container">
      <Nuxt />
    </main>

    <!-- Footer -->
    <Footer />
  </div>
</template>

<script>
import Header from '@/components/web/header.vue'
import Footer from '@/components/web/footer.vue'

export default {
  layout: 'default', // Menyatakan ini adalah layout utama
  components: {
    Header,
    Footer
  }
}
</script>

<style scoped>
.container {
  min-height: 80vh; /* Agar konten tidak terlalu kecil */
  padding-top: 20px;
}
</style>
