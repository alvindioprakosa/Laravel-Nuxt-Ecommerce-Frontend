<template>
  <header class="section-header fixed-top">
    <!-- Header Main -->
    <section class="header-main border-bottom">
      <div class="container-fluid">
        <div class="row align-items-center">
          <!-- Logo -->
          <div class="col-lg-3 col-sm-4 col-md-4 col-5"> 
            <nuxt-link to="/" class="brand-wrap">
              <img src="/images/xiaomi.png" width="35" class="bg-light p-2 rounded">
              <span class="logo">MI STORE</span>
            </nuxt-link>
          </div>

          <!-- Search Desktop -->
          <div class="col-lg-4 col-xl-5 col-sm-8 col-md-4 d-none d-md-block">
            <div class="search-wrap">
              <div class="input-group w-100">
                <input type="text" class="form-control search-form" v-model="search" @keypress.enter="searchData" placeholder="mau belanja apa hari ini ?" />
                <div class="input-group-append">
                  <button @click="searchData" class="btn btn-primary search-button">
                    <i class="fa fa-search"></i>
                  </button>
                </div>
              </div>
            </div>
          </div>

          <!-- Cart -->
          <div class="col-lg-5 col-xl-4 col-sm-8 col-md-4 col-7">
            <div class="d-flex justify-content-end">
              <nuxt-link :to="{ name: 'cart' }" class="btn search-button btn-md ml-4">
                <i class="fa fa-shopping-cart"></i> 
                <span class="ml-2">{{ cartTotal }}</span> | Rp. {{ formatPrice(cartPrice) }}
              </nuxt-link>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Navbar -->
    <nav class="navbar navbar-expand-md navbar-main border-bottom p-2">
      <div class="container-fluid">
        <!-- Search Mobile -->
        <div class="d-md-none my-2 w-100">
          <div class="input-group">
            <input type="search" class="form-control" v-model="search" @keypress.enter="searchData" placeholder="mau belanja apa hari ini ?" />
            <div class="input-group-append">
              <button @click="searchData" class="btn btn-warning"><i class="fa fa-search"></i></button>
            </div>
          </div>
        </div>

        <!-- Toggler for Mobile -->
        <button class="navbar-toggler collapsed" type="button" data-toggle="collapse" data-target="#dropdown6">
          <span class="navbar-toggler-icon"></span>
        </button>

        <!-- Menu Items -->
        <div class="navbar-collapse collapse" id="dropdown6">
          <ul class="navbar-nav mr-auto">
            <!-- Kategori Dropdown -->
            <li class="nav-item dropdown">
              <a class="nav-link dropdown-toggle" href="#" data-toggle="dropdown">
                <i class="fa fa-list-ul"></i> KATEGORI
              </a>
              <div class="dropdown-menu">
                <nuxt-link
                  v-for="category in categories"
                  :key="category.id"
                  :to="{ name: 'categories-slug', params: { slug: category.slug } }"
                  class="dropdown-item"
                >
                  <img :src="category.image" width="50"> {{ category.name }}
                </nuxt-link>
                <div class="dropdown-divider"></div>
                <nuxt-link to="/categories" class="dropdown-item text-center">
                  LIHAT SEMUA KATEGORI <i class="fa fa-long-arrow-alt-right"></i>
                </nuxt-link>
              </div>
            </li>

            <!-- Menu Utama -->
            <li class="nav-item">
              <nuxt-link to="/products" class="nav-link"><i class="fa fa-shopping-bag"></i> SEMUA PRODUK</nuxt-link>
            </li>
            <li class="nav-item">
              <a href="#" class="nav-link"><i class="fa fa-info-circle"></i> TENTANG</a>
            </li>
            <li class="nav-item">
              <a href="#" class="nav-link"><i class="fa fa-comments"></i> KONTAK</a>
            </li>
          </ul>

          <!-- Auth Links -->
          <ul class="navbar-nav ml-auto">
            <li class="nav-item" v-if="!$auth.loggedIn">
              <nuxt-link to="/customer/login" class="nav-link">
                <i class="fa fa-user-circle"></i> ACCOUNT
              </nuxt-link>
            </li>
            <li class="nav-item" v-if="$auth.loggedIn">
              <nuxt-link to="/customer/dashboard" class="nav-link">
                <i class="fa fa-tachometer-alt"></i> DASHBOARD
              </nuxt-link>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  data() {
    return {
      search: ''
    };
  },
  async fetch() {
    await this.$store.dispatch('web/category/getCategoriesData');
    if (this.$auth.loggedIn && this.$auth.strategy.name === 'customer') {
      await this.$store.dispatch('web/cart/getCartsData');
      await this.$store.dispatch('web/cart/getCartPrice');
    }
  },
  computed: {
    categories() {
      return this.$store.state.web.category.categories;
    },
    cartPrice() {
      return this.$store.state.web.cart.cartPrice;
    },
    cartTotal() {
      return this.$store.state.web.cart.carts.length;
    }
  },
  methods: {
    searchData() {
      if (!this.search.trim()) return;
      this.$router.push({
        name: 'search',
        query: {
          q: this.search
        }
      });
    },
    formatPrice(value) {
      return parseInt(value).toLocaleString('id-ID');
    }
  }
};
</script>

<style scoped>
.btn {
  font-size: initial;
}
.logo {
  font-weight: bold;
  margin-left: 10px;
  font-size: 18px;
}
.search-button {
  display: flex;
  align-items: center;
}
</style>
