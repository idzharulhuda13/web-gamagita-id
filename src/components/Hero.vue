<template>
    <div>
        <!-- Hero Section Begin -->
        <section class="hero-section">
            <carousel class="hero-items" :items="1" :nav="false">
                <div class="single-hero-items set-bg" style="background-image: url('/img/Bgamagita_1.jpg')">
                    <div class="container">
                        <div class="row">
                            <div class="col-lg-5">
                                <span style="font-size: 25px">Happy</span>
                                <h1>Eid Mubarok</h1>
                                <p>
                                    Minal 'Aidin wal-Faizin
                                </p>
                                <a href="#" class="primary-btn">Shop Now</a>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="single-hero-items set-bg" style="background-image: url('/img/Bgamagita_2.jpg')">
                    <div class="container">
                        <div class="row">
                            <div class="col-lg-5">
                                <span style="font-size: 25px">Happy</span>
                                <h1>Eid Mubarok</h1>
                                <p>
                                    Minal 'Aidin wal-Faizin
                                </p>
                                <a href="#" class="primary-btn">Shop Now</a>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="single-hero-items set-bg" style="background-image: url('/img/Bgamagita_3.jpg')">
                    <div class="container">
                        <div class="row">
                            <div class="col-lg-5">
                                <span style="font-size: 25px">Happy</span>
                                <h1>Eid Mubarok</h1>
                                <p>
                                    Minal 'Aidin wal-Faizin
                                </p>
                                <a href="#" class="primary-btn">Shop Now</a>
                            </div>
                        </div>
                    </div>
                </div>
            </carousel>
        </section>
        <!-- Hero Section End -->
    </div>
</template>

<script>

import carousel from 'vue-owl-carousel';

export default {
  name: 'Hero',
  props: {
    msg: String
  },
  components: {
    carousel
    // HelloWorld
  }
}
</script>