<template>
    <div>
        <footer class="footer-section">
            <div class="container">
                <div class="row">
                    <div class="col-lg-5">
                        <div class="footer-left text-left">
                            <div class="footer-logo">
                                <a href="#"><img src="img/logo_gamagita2.png" alt="" /></a>
                            </div>
                            <ul>
                                <li>Address: Halim, Jakarta</li>
                                <li>Phone: +62851 5646 5903</li>
                                <li>Email: gamagita.id@gmail.com</li>
                            </ul>
                            <div class="footer-social">
                                <a href="#"><i class="fa fa-facebook"></i></a>
                                <a href="#"><i class="fa fa-instagram"></i></a>
                                <a href="#"><i class="fa fa-twitter"></i></a>
                                <a href="#"><i class="fa fa-pinterest"></i></a>
                            </div>
                        </div>
                    </div>
                    <div class="col-lg-3 offset-lg-1">
                        <div class="footer-widget text-left">
                            <h5>Information</h5>
                            <ul>
                                <li><a href="#">About Us</a></li>
                                <li><a href="#">Checkout</a></li>
                                <li><a href="#">Contact</a></li>
                                <li><a href="#">Serivius</a></li>
                            </ul>
                        </div>
                    </div>
                    <div class="col-lg-3">
                        <div class="footer-widget text-left">
                            <h5>My Account</h5>
                            <ul>
                                <li><a href="#">My Account</a></li>
                                <li><a href="#">Contact</a></li>
                                <li><a href="#">Shopping Cart</a></li>
                                <li><a href="#">Shop</a></li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
            <div class="copyright-reserved">
                <div class="container">
                    <div class="row">
                        <div class="col-lg-12">
                            <div class="copyright-text">
                                Copyright &copy;2021
                                All rights reserved | Gamagita
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </footer>
    </div>
</template>

<script>

export default {
  name: 'Footer',
  props: {
    msg: String
  },
}

</script>