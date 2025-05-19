<template>
  <footer
    class="pt-5"
    style="background: #fff; border-top: 5px solid #e64a1a;"
  >
    <div class="container-fluid">
      <div class="row">
        <!-- Tentang -->
        <div class="col-md-5 mb-4">
          <h4 class="font-weight-bold">TENTANG</h4>
          <hr style="border-top: 3px solid #e2e8f0; border-radius: 0.5rem;" />
          <p>
            Mi Store Official Terpercaya di Indonesia. Jual Beli Aman &amp; Harga Termurah!
            Belanja sekarang.
          </p>
        </div>

        <!-- Metode Pembayaran -->
        <div class="col-md-3 mb-4">
          <h4 class="font-weight-bold">METODE PEMBAYARAN</h4>
          <hr style="border-top: 3px solid #e2e8f0; border-radius: 0.5rem;" />
          <div class="row">
            <div
              v-for="(payment, index) in paymentMethods"
              :key="index"
              class="col-md-4 col-4 mb-3"
            >
              <div class="card rounded">
                <div class="card-body p-2 text-center">
                  <img :src="payment.src" :alt="payment.name" :style="{ width: payment.width }" />
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Jam Operasional -->
        <div class="col-md-4 mb-4">
          <h4 class="font-weight-bold">JAM OPERASIONAL</h4>
          <hr style="border-top: 3px solid #e2e8f0; border-radius: 0.5rem;" />
          <p>
            <i class="fa fa-clock"></i> Toko Buka Setiap Hari: <br /><br />
            <strong>Senin - Jum'at</strong> ( 07.00 s/d 19.00 ) <br />
            <strong>Sabtu - Minggu</strong> ( 07.00 s/d 16.00 )
          </p>
        </div>
      </div>

      <!-- Copyright -->
      <div class="row text-center mt-3 pb-3">
        <div class="col-md-12">
          <hr />
          © <strong>MI STORE</strong> 2021 • Hak Cipta Dilindungi
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  data() {
    return {
      paymentMethods: [
        { name: 'BCA', src: '/images/payment/BCA.png', width: '50px' },
        { name: 'BNI', src: '/images/payment/BNI.png', width: '45px' },
        { name: 'BRI', src: '/images/payment/BRI.png', width: '60px' },
        { name: 'GOPAY', src: '/images/payment/GOPAY.png', width: '60px' },
        { name: 'Indomaret', src: '/images/payment/indomaret-logo.png', width: '60px' },
        { name: 'ATM Bersama', src: '/images/payment/atm-bersama.jpg', width: '40px' },
      ],
    };
  },
};
</script>

<style scoped>
footer h4 {
  color: #333;
}

footer p {
  color: #555;
  font-size: 14px;
}
</style>
<template>
  <footer
    class="pt-5"
    style="background: #fff; border-top: 5px solid #e64a1a;"
  >
    <div class="container-fluid">
      <div class="row">
        <!-- Tentang -->
        <div class="col-md-5 mb-4">
          <h4 class="font-weight-bold">TENTANG</h4>
          <hr style="border-top: 3px solid #e2e8f0; border-radius: 0.5rem;" />
          <p>
            Mi Store Official Terpercaya di Indonesia. Jual Beli Aman &amp; Harga Termurah!
            Belanja sekarang.
          </p>
        </div>

        <!-- Metode Pembayaran -->
        <div class="col-md-3 mb-4">
          <h4 class="font-weight-bold">METODE PEMBAYARAN</h4>
          <hr style="border-top: 3px solid #e2e8f0; border-radius: 0.5rem;" />
          <div class="row">
            <div
              v-for="(payment, index) in paymentMethods"
              :key="index"
              class="col-md-4 col-4 mb-3"
            >
              <div class="card rounded">
                <div class="card-body p-2 text-center">
                  <img :src="payment.src" :alt="payment.name" :style="{ width: payment.width }" />
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Jam Operasional -->
        <div class="col-md-4 mb-4">
          <h4 class="font-weight-bold">JAM OPERASIONAL</h4>
          <hr style="border-top: 3px solid #e2e8f0; border-radius: 0.5rem;" />
          <p>
            <i class="fa fa-clock"></i> Toko Buka Setiap Hari: <br /><br />
            <strong>Senin - Jum'at</strong> ( 07.00 s/d 19.00 ) <br />
            <strong>Sabtu - Minggu</strong> ( 07.00 s/d 16.00 )
          </p>
        </div>
      </div>

      <!-- Copyright -->
      <div class="row text-center mt-3 pb-3">
        <div class="col-md-12">
          <hr />
          © <strong>MI STORE</strong> 2021 • Hak Cipta Dilindungi
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  data() {
    return {
      paymentMethods: [
        { name: 'BCA', src: '/images/payment/BCA.png', width: '50px' },
        { name: 'BNI', src: '/images/payment/BNI.png', width: '45px' },
        { name: 'BRI', src: '/images/payment/BRI.png', width: '60px' },
        { name: 'GOPAY', src: '/images/payment/GOPAY.png', width: '60px' },
        { name: 'Indomaret', src: '/images/payment/indomaret-logo.png', width: '60px' },
        { name: 'ATM Bersama', src: '/images/payment/atm-bersama.jpg', width: '40px' },
      ],
    };
  },
};
</script>

<style scoped>
footer h4 {
  color: #333;
}

footer p {
  color: #555;
  font-size: 14px;
}
</style>
