<template>
  <div class="c-app">
    <div class="c-sidebar c-sidebar-dark c-sidebar-fixed c-sidebar-lg-show" id="sidebar">
      <div class="c-sidebar-brand d-lg-down-none">
        <img src="/images/xiaomi.png" class="bg-light rounded shadow-sm p-2" width="35" alt="Logo MI Store">
        <span class="ml-2 font-weight-bold">MI STORE</span>
      </div>

      <!-- Sidebar -->
      <Sidebar />
    </div>

    <div class="c-wrapper c-fixed-components">
      <!-- Header -->
      <Header />

      <div class="c-body">
        <!-- Content -->
        <Nuxt />
        
        <!-- Footer -->
        <footer class="c-footer">
          <div><strong>MI STORE</strong> &copy; {{ new Date().getFullYear() }} - yanafriyoko.com.</div>
          <div class="ml-auto">
            Template by&nbsp;<a href="https://coreui.io/" target="_blank" rel="noopener noreferrer">CoreUI</a>
          </div>
        </footer>
      </div>
    </div>
  </div>
</template>

<script>
import Header from '@/components/admin/Header.vue';
import Sidebar from '@/components/admin/Sidebar.vue';

export default {
  middleware: 'isAdmin', // Pastikan middleware sudah dibuat di middleware/isAdmin.js

  components: {
    Header,
    Sidebar
  }
}
</script>

<style scoped>
/* Tambahkan styling jika perlu */
</style>
