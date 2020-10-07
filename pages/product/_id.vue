<template>
    <div class="container-fluid">
        <div class="row align-items-center">
            <nuxt-link to="/" class="pl-4 mt-3 d-inline-block" style="position:fixed; top: 0; left: 0; z-index: 99;">
                <img src="~/assets/images/arrow-left-custom.svg" alt="" width="28">
            </nuxt-link>
            <!-- <a href="<?php echo site_url(); ?>" >
                <img src="~/assets/images/arrow-left-custom.svg" alt="" width="28">
            </a> -->
            <div class="col-md-6">
                <img :src="imageProduct(item.image)" :alt="item.name" class="img-fluid mt-5">
            </div>
            <div class="col-md-6">
                <div class="summary text-center p-4" v-bind:class="[isActive ? 'detail-active' : '']">
                    <div class="wrap-spin mb-3" @click.prevent="toggleClass()">
                        <span></span>
                        <span></span>
                        <span></span>
                        <span></span>
                    </div>
                    <h1 class="font-weight-bold mb-3">{{ item.name }}</h1>
                    <div class="detail">
                        <p class="pre-formatted">{{ item.description }}</p>
                        <h4 class="font-weight-bold text-red my-4">{{ item.price / 100000 | currency }}</h4>
                        <a :href="waLink" target="_blank" class="btn btn-custom bg-white text-success font-weight-bold d-block w-100">WhatsApp</a>
                        <a :href="shopeeLink" target="_blank" class="btn btn-custom bg-white text-orange font-weight-bold d-block w-100 mt-4">Beli Via Shopee</a>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    data () {
        return {
            isActive: false,
            item: '',
        }
    },
    mounted () {
        axios.post('http://shopee.test/product-detail.php', null, {params: {'id': this.$route.params.id}})
        .then((response) => {
            this.item = response.data.item;
        })
    },
    methods: {
        toggleClass: function(e) {
            this.isActive = !this.isActive;
        },
        imageProduct: function(img) {
            return `https://cf.shopee.co.id/file/${img}`;
        }
    },
    computed: {
        waLink: function() {
            return `https://api.whatsapp.com/send?phone=6287875221888&text=Saya tertarik dengan produk ${this.item.name}.`;
        },
        shopeeLink: function() {
            return `https://shopee.co.id/${this.item.name}-i.${this.item.shopid}.${this.item.itemid}`;
        }
    }
}
</script>

<style>
.pre-formatted {
  white-space: pre;
}
.summary{
    background-color: rgba(255, 170, 170, 0.8);
    backdrop-filter: blur(4px);
    border-radius: 30px 0 0 30px;
    color: #fff;
}
@media screen and (max-width: 768px){
    .summary{
        border-radius: 30px 30px 0 0;
        position: fixed;
        bottom: 0;
        left: 0;
        width: 100%;
    }
    .detail{
        display: none;
    }
    .summary.detail-active .detail{
        display: block;
    }
}
</style>