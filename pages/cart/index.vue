<template>
  <div>
    <table>
      <tbody>
        <tr v-for="cart in carts" :key="cart.id" style="background: #edf2f7;">
          <td><img :src="cart.image" alt="cart image" class="img-thumbnail"></td>
          <td>{{ cart.name }}</td>
          <td>{{ cart.quantity }}</td>
          <td>Rp. {{ formattedCartPrice }}</td>
        </tr>
      </tbody>
    </table>

    <div v-if="!isValidForm">
      <p class="error">All fields are required!</p>
    </div>

    <button @click="checkout">Checkout</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      carts: [], // Data from store
      customer: {
        name: '',
        phone: '',
        address: ''
      },
      cartPrice: 0,
      grandTotal: 0,
      courier: { courier_name: '', courier_cost: 0 },
      cartWeight: 0,
      validation: {
        name: false,
        phone: false,
        address: false
      }
    };
  },
  computed: {
    formattedCartPrice() {
      return this.formatPrice(this.cartPrice);
    },
    formattedGrandTotal() {
      return this.formatPrice(this.grandTotal);
    },
    formattedCourierCost() {
      return this.formatPrice(this.courier.courier_cost);
    },
    isValidForm() {
      return this.customer.name && this.customer.phone && this.customer.address;
    }
  },
  methods: {
    formatPrice(price) {
      return new Intl.NumberFormat('id-ID', { style: 'currency', currency: 'IDR' }).format(price);
    },
    async asyncData({ store }) {
      try {
        await Promise.all([
          store.dispatch('web/cart/getCartsData'),
          store.dispatch('web/rajaongkir/getProvincesData')
        ]);
      } catch (error) {
        console.error('Error fetching data:', error);
      }
    },
    validateForm() {
      this.validation.name = !this.customer.name;
      this.validation.phone = !this.customer.phone;
      this.validation.address = !this.customer.address;

      return !this.validation.name && !this.validation.phone && !this.validation.address;
    },
    async checkout() {
      if (this.validateForm() && this.cartWeight) {
        try {
          // Logic for checkout
          await this.$store.dispatch('web/cart/checkout', {
            customer: this.customer,
            cartDetails: this.carts,
            courier: this.courier
          });

          // Success message or redirect
          this.$swal.fire('Success', 'Checkout successful!', 'success');
        } catch (error) {
          this.$swal.fire('Error', 'An error occurred during checkout!', 'error');
        }
      } else {
        this.$swal.fire('Warning', 'Please fill in all the required fields!', 'warning');
      }
    },
    async removeCart(cartId) {
      try {
        await this.$store.dispatch('web/cart/removeCart', { cart_id: cartId });
        // Update the carts data or show success
      } catch (error) {
        this.$swal.fire('Error', 'There was an error removing the cart item.', 'error');
      }
    }
  },
  created() {
    this.asyncData({ store: this.$store });
  }
};
</script>

<style scoped>
/* Style for error message */
.error {
  color: red;
  font-weight: bold;
}
</style>
