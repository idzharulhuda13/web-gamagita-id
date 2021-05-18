<template>
    <div class="shopping">
        <Header></Header>

        <!-- Breadcrumb Section Begin -->
        <div class="breacrumb-section text-left">
            <div class="container">
                <div class="row">
                    <div class="col-lg-12">
                        <div class="breadcrumb-text product-more">
                            <router-link to="/"><i class="fa fa-home"></i> Home</router-link>
                            <span>Shopping Cart</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <!-- Breadcrumb Section Begin -->

        <!-- Shopping Cart Section Begin -->
        <section class="shopping-cart spad">
            <div class="container">
                <div class="row">
                    <div class="col-lg-8">
                        <div class="row">
                            <div class="col-lg-12">
                                <div class="cart-table">
                                    <table>
                                        <thead>
                                            <tr>
                                                <th>Image</th>
                                                <th class="p-name text-center">Product Name</th>
                                                <th>Price</th>
                                                <th>Action</th>
                                            </tr>
                                        </thead>
                                        <tbody>
                                            <tr v-for="cart in userCart" :key="cart.id">
                                                <td class="cart-pic first-row">
                                                    <img class="img-cart" :src="cart.photo" />
                                                </td>
                                                <td class="cart-title first-row text-center">
                                                    <h5>{{cart.name}}</h5>
                                                </td>
                                                <td class="p-price first-row">${{cart.price}}</td>
                                                <td class="delete-item"><a @click="removeItem(cart.id)" href="#"><i class="material-icons">
                                                close
                                                </i></a></td>
                                            </tr>
                                        </tbody>
                                    </table>
                                </div>
                            </div>
                            <div class="col-lg-8 text-left">
                                <h4 class="mb-4">
                                    Informasi Pembeli:
                                </h4>
                                <div class="user-checkout">
                                    <form>
                                        <div class="form-group">
                                            <label for="namaLengkap">Nama lengkap</label>
                                            <input type="text" class="form-control" id="namaLengkap" aria-describedby="namaHelp" placeholder="Masukan Nama" v-model="customerInfo.name">
                                        </div>
                                        <div class="form-group">
                                            <label for="namaLengkap">Email Address</label>
                                            <input type="email" class="form-control" id="emailAddress" aria-describedby="emailHelp" placeholder="Masukan Email" v-model="customerInfo.email">
                                        </div>
                                        <div class="form-group">
                                            <label for="namaLengkap">No. HP</label>
                                            <input type="text" class="form-control" id="noHP" aria-describedby="noHPHelp" placeholder="Masukan No. HP" v-model="customerInfo.number">
                                        </div>
                                        <div class="form-group">
                                            <label for="alamatLengkap">Alamat Lengkap</label>
                                            <textarea class="form-control" id="alamatLengkap" rows="3" v-model="customerInfo.address"></textarea>
                                        </div>
                                    </form>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="col-lg-4 text-left">
                        <div class="row">
                            <div class="col-lg-12">
                                <div class="proceed-checkout">
                                    <ul>
                                        <li class="subtotal">ID Transaction <span>#SH12000</span></li>
                                        <li class="subtotal mt-3">Subtotal <span>${{priceTotal}}</span></li>
                                        <li class="subtotal mt-3">Pajak <span>10% = ${{tax}}</span></li>
                                        <li class="subtotal mt-3">Total Biaya <span>${{lastPrice}}</span></li>
                                        <li class="subtotal mt-3">Bank Transfer <span>Mandiri</span></li>
                                        <li class="subtotal mt-3">No. Rekening <span>2208 1996 1403</span></li>
                                        <li class="subtotal mt-3">Nama Penerima <span>Gamagita</span></li>
                                    </ul>
                                    <!-- <router-link to="/success" class="proceed-btn"> -->
                                        <a @click="checkout()" href="#" class="proceed-btn">I ALREADY PAID</a>
                                    <!-- </router-link> -->
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        <!-- Shopping Cart Section End -->
    </div>    
</template>

<script>

import Header from '@/components/Header.vue';
import axios from 'axios';

export default {
    name: "ShoppingCart",
    components: {
        Header,
    },
    data() {
        return {
            userCart: [],
            customerInfo: {
                name: '',
                email: '',
                number: '',
                address: '',
            }
        };
    },
    methods: {
      removeItem(idRemove) {
          
          //find cart data index from local storage
          let userCartStorage = JSON.parse(localStorage.getItem("userCart"));
          let itemUserCartStorage = userCartStorage.map(itemUserCartStorage => itemUserCartStorage.id);

          //compare cart index with idRemove
          let index = itemUserCartStorage.findIndex(id => id == idRemove);
          this.userCart.splice(index, 1);
          
          //save local storage after remove
          const parsed = JSON.stringify(this.userCart);
          localStorage.setItem('userCart', parsed);
          window.location.reload();
      },
      checkout() {
          let productsIds = this.userCart.map(function(product){
              return product.id
          });

          let checkoutData = {
              'name': this.customerInfo.name,
              'email': this.customerInfo.email,
              'number': this.customerInfo.number,
              'address': this.customerInfo.address,
              "transaction_total": this.lastPrice,
              "transaction_status": "PENDING",
              "transaction_details": productsIds
          };

          axios
            .post("http://127.0.0.1:8000/api/checkout", checkoutData)
            .then(() => this.$router.push("success"))
            .catch(err => console.log(err));
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
    },
    computed: {
      priceTotal() {
          return this.userCart.reduce(function(items, data){
              return items + data.price;
          }, 0);
      },
      tax() {
          return (this.priceTotal*10)/100;
      },
      lastPrice() {
          return (this.priceTotal + this.tax);
      }
    }
}
</script>

<style scoped>
.img-cart{
    width: 127px;
    height: 127px;
}
</style>