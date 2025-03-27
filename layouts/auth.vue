<template>
  <div class="c-app flex-row align-items-center">
    <div class="container">
      <div class="row justify-content-center">
        <div class="col-md-4">
          <main>
            <Nuxt />
          </main>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  layout: 'auth', // Gunakan layout khusus jika ini hanya untuk halaman auth
}
</script>

<style scoped>
body {
  font-family: 'Quicksand', sans-serif;
  font-size: initial !important;
}

.form-control {
  height: initial;
  font-size: 1rem;
}

.c-app {
  background-color: #BCCAD8 !important;
  min-height: 100vh; /* Agar background tetap penuh */
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
