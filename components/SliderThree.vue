<template>
  <section class="banner-section banner-three">
    <div class="banner-carousel-three owl-theme owl-carousel">
      <client-only>
        <carousel :items="1" :autoplay="true" :nav="false">
          <!-- Slide Item -->
          <div class="slide-item">
            <div
              class="image-layer"
              style="background-image: url(/assets/images/main-slider/slide_v3_1.jpeg);"
            ></div>
            <div class="auto-container">
              <div class="content-box">
                <div class="content">
                  <div class="inner">
                    <!-- <div class="big_text">
                      <h2>Agroethical</h2>
                    </div>
                    <div class="sub-title">
                      We are a leading supplier of livestock from Europe to the
                      world!
                    </div>
                    <div class="link-box">
                      <nuxt-link to="/about" class="thm-btn"
                        >Discover More</nuxt-link
                      >
                    </div> -->
                  </div>
                </div>
              </div>
            </div>
          </div>
          <!-- Slide Item -->
          <div class="slide-item">
            <div
              class="image-layer"
              style=" background-image: url(/assets/images/main-slider/slide_v3_2_1.jpeg);"
            ></div>
            <div class="auto-container">
              <div class="content-box">
                <div class="content">
                  <div class="inner">
                    <!-- <div class="big_text">
                      <h2>Agroethical</h2>
                    </div>
                    <div class="sub-title">Your trusted partner in livestock exports.
                    </div>
                    <div class="link-box">
                      <nuxt-link to="/about" class="thm-btn"
                        >Discover More</nuxt-link
                      >
                    </div> -->
                  </div>
                </div>
              </div>
            </div>
          </div>
          <!-- Slide Item -->
          <div class="slide-item">
            <div
              class="image-layer"
              style=" background-image: url(/assets/images/shipping/shipping-header2.jpeg);"
            ></div>
            <div class="auto-container">
              <div class="content-box">
                <div class="content">
                  <div class="inner">
                    <!-- <div class="big_text">
                      <h2>Agroethical</h2>
                    </div>
                    <div class="sub-title">Your trusted partner in livestock exports.
                    </div>
                    <div class="link-box">
                      <nuxt-link to="/about" class="thm-btn"
                        >Discover More</nuxt-link
                      >
                    </div> -->
                  </div>
                </div>
              </div>
            </div>
          </div>
        </carousel>
      </client-only>
    </div>
  </section>
</template>

<script>
export default {
  name: "SliderThree",
};
</script>
