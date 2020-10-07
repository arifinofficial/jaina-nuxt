<template>
  <div>
    <header class="">
    <div class="row vh-100 no-gutters">
        <div class="position-absolute w-100 circle-wrap">
            <div class="row no-gutters">
                <div class="col-3">
                    <span class="circle d-flex align-items-center justify-content-center">
                        <p>100% <br> Original</p>
                    </span>
                </div>
                <div class="col-3">
                    <span class="circle d-flex align-items-center justify-content-center">
                        <p>COD</p>
                    </span>
                </div>
                <div class="col-3">
                    <span class="circle d-flex align-items-center justify-content-center">
                        <p>Best <br> Quality</p>
                    </span>
                </div>
                <div class="col-3">
                    <span class="circle d-flex align-items-center justify-content-center">
                        <p>Local <br> Brand</p>
                    </span>
                </div>
            </div>
        </div>
        <div class="col-6 left">
            <div class="d-flex align-items-start flex-column h-100 container">
                <div class="mb-auto mx-auto mt-4">
                    <h1 class="logo text-white">JAINA.CO</h1>
                </div>
                <div class="mb-auto text-white">
                    <h2>Premium Women’s Clothes</h2>
                    <p>Setelan Jaina dengan motif floral yang menawan dan sangat nyaman dipakai di segala aktivitas</p>
                </div>
            </div>
        </div>
        <div class="col-6 right">
            <div class="h-100 bg-header"></div>
        </div>
    </div>
</header>

<section class="section-default detail-jaina">
    <div class="container">
        <h3 class="font-weight-bold mb-5 mt-5">Detail Jaina</h3>
        <div class="row">
            <div class="col-md-3 mb-4 md-mb-0">
                <div class="wrap-img-detail border-radius-20">
                    <img src="~/assets/images/kain-premium.jpg" alt="" class="img-fluid border-radius-20">
                    <span class="position-absolute w-100 d-block">
                        Kain Premium Rayon (bahan halus dan lembut)
                    </span>
                </div>
            </div>
            <div class="col-md-3 mb-4 md-mb-0">
                <div class="wrap-img-detail border-radius-20">
                    <img src="~/assets/images/colorful-.jpg" alt="" class="img-fluid border-radius-20">
                    <span class="position-absolute w-100 d-block">
                        Colorful and Beautiful Motifs
                    </span>
                </div>
            </div>
            <div class="col-md-3 mb-4 md-mb-0">
                <div class="wrap-img-detail border-radius-20">
                    <img src="~/assets/images/varian.jpg" alt="" class="img-fluid border-radius-20">
                    <span class="position-absolute w-100 d-block">
                        Varian Jumsuit, dress, sleeping dress, skirt, pants, cullotte, top
                    </span>
                </div>
            </div>
            <div class="col-md-3 mb-4 md-mb-0">
                <div class="wrap-img-detail border-radius-20">
                    <img src="~/assets/images/one-sizeItem.jpg" alt="" class="img-fluid border-radius-20">
                    <span class="position-absolute w-100 d-block">
                        One Size/Item
                    </span>
                </div>
            </div>
        </div>
        <div class="text-center mt-5">
            <button class="btn btn-custom font-weight-bold">FREE ONGKIR</button>
        </div>
    </div>
</section>

<section class="section-default all-product">
    <div class="container">
        <div class="row">
          <div v-for="item in items" v-bind:key="item.itemid" class="col-md-3 text-center">
            <nuxt-link :to="{name: 'product-id', params: {'id': item.itemid}}">
              <div class="border-radius-20 product-list pb-3 mb-3">
                <img v-lazy="imageProduct(item.image)" :alt="item.name" class="img-fluid">
                <h2 class="title-product my-3">{{ item.name }}</h2>
                <span class="mb-3 d-block">{{ item.price / 100000 | currency }}</span>
              </div>
            </nuxt-link>
          </div>
        </div>
    </div>
</section>

<section class="section-default pt-0">
    <div class="container">
        <div class="p-4 bg-pink text-white font-italic font-weight-bold text-center border-radius-20 mb-4 min-height">
            <p class="m-0">PRODUK PALING DISUKAI WANITA INDONESIA SAAT INI SEGERA AMBIL PRODUK YANG KAMU SUKAI</p>
        </div>
        <div class="p-4 bg-red text-center text-white border-radius-20">
            <h2 class="font-weight-bold mb-0">STOCK TERBATAS</h2>
        </div>
    </div>
</section>
<Footer />
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      items: ''
    }
  },
  mounted () {
    axios.get('http://shopee.test/product.php')
    .then((response) => {
      this.items = response.data.items;
    })
  },
  methods: {
    imageProduct: function(img) {
      return `https://cf.shopee.co.id/file/${img}_tn`;
    }
  },
  computed: {
    
  }
}
</script>

<style>
.bg-header{
  background: url('~@/assets/images/yellow-lauren.jpg');
}

header .left{
    background: rgba(255, 170, 170, 0.5);
    backdrop-filter: blur(5px);
    z-index: 1;
}

header .right{
    z-index: 0;
}

header .logo{
    font-weight: bold;
    font-size: 20px;
}

header h2{
    font-size: 50px;
    font-weight: bold;
}

header .right .bg-header{
    background-repeat: no-repeat !important;
    background-size: cover !important;
    background-position: 45% !important;
    margin-left: -45px;
}

header .circle{
    background-color: #B04C4C;
    width: 80px;
    height: 80px;
    display: block;
    border-radius: 50%;
    font-size: 12px !important;
    color: #fff;
    text-align: center;
    margin: auto;
    box-shadow: 0px 0px 20px 4px rgba(222, 146, 146, 0.6);
}

header .circle p{
    margin: auto 0;
    display: inline-block;
}

header .circle-wrap{
    z-index: 2;
    bottom: 50px;
}

.all-product a{
    color: #000;
    text-decoration: none;
}

.title-product{
  font-size: 16px;
}

.product-list{
  box-shadow: 0px 0px 25px 1px rgba(0, 0, 0, 0.05);
  transition: all .2s;
}

.product-list:hover{
  box-shadow: 0px 0px 25px 1px rgba(0,0,0,0.15);
  transform: scale(1.02);
}

.product-list img{
  border-radius: 25px 25px 0 0;
}
</style>
