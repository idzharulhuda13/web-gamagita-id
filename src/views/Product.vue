<template>
  <div class="product">

    <Header></Header>
    <!-- Breadcrumb Section Begin -->
    <div class="breacrumb-section text-left">
        <div class="container">
            <div class="row">
                <div class="col-lg-12">
                    <div class="breadcrumb-text product-more">
                        <router-link to="/"><i class="fa fa-home"></i> Home</router-link>
                        <span>Detail</span>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <!-- Breadcrumb Section Begin -->

    <!-- Product Shop Section Begin -->
    <section class="product-shop spad page-details">
        <div class="container">
            <div class="row">
                <div class="col-lg-12">
                    <div class="row">
                        <div class="col-lg-6">
                            <div class="product-pic-zoom">
                                <img class="product-big-img" :src="gambar_default" alt="" />
                            </div>
                            <div class="product-thumbs" v-if="productDetails.galleries.length > 0">
                                <carousel :dots="false" :nav="false" class="product-thumbs-track ps-slider">
                                    <div v-for="images in productDetails.galleries" :key="images.id" class="pt" @click="changeImage(images.photo)" :class="images.photo == gambar_default ? 'active' : ''">
                                        <img :src="images.photo" alt="" />
                                    </div>
                                </carousel>
                            </div>
                        </div>
                        <div class="col-lg-6">
                            <div class="product-details text-left">
                                <div class="pd-title">
                                    <span>{{productDetails.type}}</span>
                                    <h3>{{productDetails.name}}</h3>
                                </div>
                                <div class="pd-desc">
                                    <p v-html="productDetails.description"></p>
                                    <h4>${{productDetails.price}}</h4>
                                </div>
                                <div class="quantity">
                                    <router-link to="/shoppingcart">
                                    <a @click="saveCart(productDetails.id, productDetails.name, productDetails.price, productDetails.galleries[0].photo)" href="#" class="primary-btn pd-cart">Add To Cart</a>
                                    </router-link>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
    <!-- Product Shop Section End -->

    <RelatedProduct></RelatedProduct>

    <Footer></Footer>

  </div>
</template>

<script>

import Header from '@/components/Header.vue';
import Footer from '@/components/Footer.vue';
import RelatedProduct from '@/components/RelatedProduct.vue';
import carousel from 'vue-owl-carousel';

import axios from 'axios';

export default {
    name: 'Product',
    components: {
        Header,
        Footer,
        RelatedProduct,
        carousel
    },
    data() {
        return {
            gambar_default: '',
            productDetails: [],
            userCart: []
        }
    },
    methods: {
        changeImage(urlImage) {
            this.gambar_default = urlImage;
        },
        setDataPictures(data) {
            this.productDetails = data;
            this.gambar_default = data.galleries[0].photo;
        },
        saveCart(idProduct, nameProduct, priceProduct, photoProduct) {

            var productStored = {
                "id": idProduct,
                "name": nameProduct,
                "price": priceProduct,
                "photo": photoProduct
            }

            this.userCart.push(productStored);
            const parsed = JSON.stringify(this.userCart);
            localStorage.setItem('userCart', parsed);
        }
    },
    mounted() {
        if (localStorage.getItem('userCart')) {
            try {
                this.userCart = JSON.parse(localStorage.getItem('userCart'));
            } 
            catch(e) {
                localStorage.removeItem('userCart');
            }
        }  
        axios
            .get("http://127.0.0.1:8000/api/products", {
                params: {
                    id: this.$route.params.id
                }
            })
            .then(res => (this.setDataPictures(res.data.data)))
            .catch(err => console.log(err));
  }
};
</script>

<style scoped>
.product-thumbs .pt{
    margin-right: 14px;
}
</style>