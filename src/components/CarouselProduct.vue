<template>
  <div>
    <section class="women-banner spad" id="carousel-product">
      <div class="container-fluid">
        <div class="row">
          <div class="col-lg-12 mt-5" v-if="products.length > 0">
            <carousel
              class="product-slider"
              :nav="false"
              :item="3"
              :autoplay="true"
              :dots="false"
            >
              <div
                class="product-item"
                v-for="itemProduct in products"
                :key="itemProduct.id"
              >
                <div class="pi-pic">
                  <img :src="itemProduct.galleries[0].photo" alt="" />
                  <ul>
                    <li class="w-icon active">
                      <!-- <router-link to="/"> -->
                      <a
                        @click="
                          saveCart(
                            itemProduct.id,
                            itemProduct.name,
                            itemProduct.price,
                            itemProduct.galleries[0].photo
                          )
                        "
                        href="#"
                        ><i class="icon_bag_alt"></i
                      ></a>
                      <!-- </router-link> -->
                    </li>
                    <li class="quick-view">
                      <router-link :to="'/product/' + itemProduct.id">
                        + Quick View
                      </router-link>
                    </li>
                  </ul>
                </div>
                <div class="pi-text">
                  <div class="catagory-name">{{ itemProduct.type }}</div>
                  <router-link :to="'/product/' + itemProduct.id">
                    <a href="#">
                      <h5>{{ itemProduct.name }}</h5>
                    </a>
                  </router-link>
                  <div class="product-price">
                    ${{ itemProduct.price }}
                    <span>$25.00</span>
                  </div>
                </div>
              </div>
            </carousel>
          </div>
          <div class="col-lg-12" v-else>
            <p>Produk belum tersedia untuk saat ini</p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import carousel from "vue-owl-carousel";
import axios from "axios";

export default {
  name: "CaroueselProduct",
  props: {
    msg: String,
  },
  components: {
    carousel,
  },
  data() {
    return {
      products: [],
      userCart: [],
    };
  },
  methods: {
    saveCart(idProduct, nameProduct, priceProduct, photoProduct) {
      var productStored = {
        id: idProduct,
        name: nameProduct,
        price: priceProduct,
        photo: photoProduct,
      };
      this.userCart.push(productStored);
      const parsed = JSON.stringify(this.userCart);
      localStorage.setItem("userCart", parsed);
      window.location.reload();
    },
  },
  mounted() {
    if (localStorage.getItem("userCart")) {
      try {
        this.userCart = JSON.parse(localStorage.getItem("userCart"));
      } catch (e) {
        localStorage.removeItem("userCart");
      }
    }
    axios
      .get("http://127.0.0.1:8000/api/products")
      .then((res) => (this.products = res.data.data.data))
      .catch((err) => console.log(err));
  },
};
</script>

<style scoped>
.product-item {
  margin-right: 25px;
}
</style>
