<template>
  <section class="work_one">
    <div class="container">
      <div class="block-title text-center">
        <p>how it works</p>
        <h3>follow 4 easy steps</h3>
        <div class="leaf">
          <img v-lazy-load data-src="/assets/images/resources/leaf.png" alt="leaf">
        </div>
      </div>
      <div class="row">
        <div class="col-xl-3 col-lg-3 col-md-6">
          <div class="work_one_single wow fadeInLeft" data-wow-delay="300ms">
            <div class="work_one_icon_box">
              <img v-lazy-load data-src="/assets/images/icon/needs-icon.svg" width="50" >
              <div class="work_one_count_box">
                <h5>01</h5>
              </div>
            </div>
            <div class="work_one_content">
              <h2>Specify your needs</h2>
            </div>
          </div>
        </div>
        <div class="col-xl-3 col-lg-3 col-md-6">
          <div class="work_one_single wow fadeInLeft" data-wow-delay="600ms">
            <div class="work_one_icon_box">
              <img v-lazy-load width="75" data-src="/assets/images/icon/phone-icon.png" >
              <div class="work_one_count_box">
                <h5>02</h5>
              </div>
            </div>
            <div class="work_one_content">
              <h2>Meet our expert team</h2>
            </div>
          </div>
        </div>
        <div class="col-xl-3 col-lg-3 col-md-6">
          <div class="work_one_single wow fadeInLeft" data-wow-delay="900ms">
            <div class="work_one_icon_box">
              <img v-lazy-load data-src="/assets/images/icon/quality-icon.svg" width="50" >

              <div class="work_one_count_box">
                <h5>03</h5>
              </div>
            </div>
            <div class="work_one_content">
              <h2>Select best quality in our farms</h2>
            </div>
          </div>
        </div>
        <div class="col-xl-3 col-lg-3 col-md-6">
          <div class="work_one_single last_box wow fadeInLeft" data-wow-delay="1200ms">
            <div class="work_one_icon_box">
              <img v-lazy-load width="100" data-src="/assets/images/cow-color.svg" alt="cow" >

              <div class="work_one_count_box">
                <h5>04</h5>
              </div>
            </div>
            <div class="work_one_content">
              <h2>Get the best cargo</h2>
            </div>
          </div>
        </div>
      </div>
      <div class="text-center mt-lg-5 mb-5 mb-lg-0">
        <nuxt-link to="/contact" class="thm-btn">GET A FREE QUOTE</nuxt-link>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "WorkOne"
}
</script>
