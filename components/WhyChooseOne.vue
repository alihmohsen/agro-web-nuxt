<template>
  <section class="why_choose_one">
    <div class="container">
      <div class="row">
        <div class="col-xl-6 col-lg-6 order-1 order-lg-0">
          <div class="why_choose_one_left_content">
            <div class="block-title text-left">
              <p>Why Choose us</p>
              <h3>Professional expertise at your hands!</h3>
              <div class="leaf">
                <img v-lazy-load data-src="/assets/images/resources/leaf.png" alt="leaf">
              </div>
            </div>
            <ul class="why_choose_list list-unstyled">
              <li>
                <div class="choose_count">
                  <h2>01</h2>
                </div>
                <div class="choose_text">
                  <p>We offer our clients our vast expertise in this field. However big is your project, we can handle
                    it and assure on-time delivery. </p>
                </div>
              </li>
              <li>
                <div class="choose_count">
                  <h2>02</h2>
                </div>
                <div class="choose_text">
                  <p>We have teams of experts available in multiple countries. </p>
                </div>
              </li>
              <li>
                <div class="choose_count">
                  <h2>03</h2>
                </div>
                <div class="choose_text">
                  <p>We guarantee best and most ethical sourcing of cattle and livestock.</p>
                </div>
              </li>
            </ul>
            <div class="why_choose_btn">
              <nuxt-link to="/about" class="thm-btn">Discover More</nuxt-link>
            </div>
          </div>
        </div>
        <div class="col-xl-6 col-lg-6 px-0 px-lg-3 order-0 order-lg-1 mt-4 mt-lg-0">
          <div class="why_choose_image_top">
            <div class="why_choose_image" style="background-image: url(/assets/images/resources/why_choose1_img-1.jpg)">
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "WhyChooseOne"
}
</script>

<style scoped>

</style>
