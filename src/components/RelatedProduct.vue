<template>
    <div>
        <!-- Related Products Section End -->
        <div class="related-products spad">
            <div class="container">
                <div class="row">
                    <div class="col-lg-12">
                        <div class="section-title">
                            <h2>Related Products</h2>
                        </div>
                    </div>
                </div>
                <div class="row">
                    <div class="col-lg-3 col-sm-6">
                        <div class="product-item">
                            <div class="pi-pic">
                                <img src="img/products/gamagita_bara1.jpg" alt="" />
                                <ul>
                                    <li class="w-icon active">
                                        <a href="#"><i class="icon_bag_alt"></i></a>
                                    </li>
                                    <li class="quick-view"><router-link to="/Product">+ Quick View</router-link></li>
                                </ul>
                            </div>
                            <div class="pi-text">
                                <div class="catagory-name">Scarf</div>
                                <a href="#">
                                    <h5>Bara</h5>
                                </a>
                                <div class="product-price">
                                    $15.00
                                    <span>$35.00</span>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="col-lg-3 col-sm-6">
                        <div class="product-item">
                            <div class="pi-pic">
                                <img src="img/products/gamagita_tirta1.jpg" alt="" />
                                <ul>
                                    <li class="w-icon active">
                                        <a href="#"><i class="icon_bag_alt"></i></a>
                                    </li>
                                    <li class="quick-view"><a href="#">+ Quick View</a></li>
                                </ul>
                            </div>
                            <div class="pi-text">
                                <div class="catagory-name">Scarf</div>
                                <a href="#">
                                    <h5>Tirta</h5>
                                </a>
                                <div class="product-price">
                                    $15.00
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="col-lg-3 col-sm-6">
                        <div class="product-item">
                            <div class="pi-pic">
                                <img src="img/products/gamagita_puspa1.jpg" alt="" />
                                <ul>
                                    <li class="w-icon active">
                                        <a href="#"><i class="icon_bag_alt"></i></a>
                                    </li>
                                    <li class="quick-view"><a href="#">+ Quick View</a></li>
                                </ul>
                            </div>
                            <div class="pi-text">
                                <div class="catagory-name">Scarf</div>
                                <a href="#">
                                    <h5>Puspa</h5>
                                </a>
                                <div class="product-price">
                                    $15.00
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="col-lg-3 col-sm-6">
                        <div class="product-item">
                            <div class="pi-pic">
                                <img src="img/products/gamagita_patera1.jpg" alt="" />
                                <ul>
                                    <li class="w-icon active">
                                        <a href="#"><i class="icon_bag_alt"></i></a>
                                    </li>
                                    <li class="quick-view"><a href="#">+ Quick View</a></li>
                                </ul>
                            </div>
                            <div class="pi-text">
                                <div class="catagory-name">Scarf</div>
                                <a href="#">
                                    <h5>Patera</h5>
                                </a>
                                <div class="product-price">
                                    $15.00
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <!-- Related Products Section End -->
    </div>
</template>

<script>

export default {
  name: 'RelatedProduct',
  props: {
    msg: String
  },
}
</script>