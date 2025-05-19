<template>
  <div class="card border-0 rounded shadow-sm border-top-orange">
    <div class="card-body">
      <h5>MAIN MENU</h5>
      <hr>
      <ul class="list-group">

        <nuxt-link
          :to="{ name: 'customer-dashboard' }"
          class="list-group-item text-decoration-none text-dark text-uppercase"
        >
          <i class="fa fa-tachometer-alt"></i> Dashboard
        </nuxt-link>

        <nuxt-link
          :to="{ name: 'customer-invoices' }"
          class="list-group-item text-decoration-none text-dark text-uppercase"
        >
          <i class="fa fa-shopping-cart"></i> My Orders
        </nuxt-link>

        <li
          class="list-group-item text-decoration-none text-dark text-uppercase"
          style="cursor: pointer;"
        >
          <button @click="logout" class="btn btn-link p-0 text-dark text-uppercase">
            <i class="fa fa-sign-out-alt"></i> Logout
          </button>
        </li>

      </ul>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    async logout() {
      try {
        await this.$auth.logout()
        this.$store.commit('web/cart/SET_CARTS_DATA', [])
        this.$store.commit('web/cart/SET_CART_PRICE', 0)
        this.$router.push({ name: 'customer-login' })
      } catch (error) {
        console.error('Logout failed:', error)
      }
    }
  }
}
</script>

<style scoped>
a.nuxt-link-active,
a.nuxt-link-exact-active {
  background: rgba(255, 222, 212, 0.1) !important;
  font-weight: bold;
}
</style>
