<template>
  <div class="brand-one brand-four">
    <div class="container">
      <div class="row">
        <div class="col-xl-12">
          <div class="brand-one-carousel owl-carousel">
            <client-only>
              <carousel :autoplay="true" :dots="false" :nav="false" :responsive="{0: {items: 1},640: {items: 2},992: {items: 3},1024: {items: 5}}">
                <div class="single_brand_item">
                  <a href="#"><img v-lazy-load  data-src="/assets/images/resources/brand-1-1.png" alt="brand"></a>
                </div>
                <div class="single_brand_item">
                  <a href="#"><img v-lazy-load  data-src="/assets/images/resources/brand-1-2.png" alt="brand"></a>
                </div>
                <div class="single_brand_item">
                  <a href="#"><img v-lazy-load  data-src="/assets/images/resources/brand-1-3.png" alt="brand"></a>
                </div>
                <div class="single_brand_item">
                  <a href="#"><img v-lazy-load  data-src="/assets/images/resources/brand-1-4.png" alt="brand"></a>
                </div>
                <div class="single_brand_item">
                  <a href="#"><img v-lazy-load  data-src="/assets/images/resources/brand-1-5.png" alt="brand"></a>
                </div>
                <div class="single_brand_item">
                  <a href="#"><img v-lazy-load  data-src="/assets/images/resources/brand-1-1.png" alt="brand"></a>
                </div>
                <div class="single_brand_item">
                  <a href="#"><img v-lazy-load  data-src="/assets/images/resources/brand-1-2.png" alt="brand"></a>
                </div>
                <div class="single_brand_item">
                  <a href="#"><img v-lazy-load  data-src="/assets/images/resources/brand-1-3.png" alt="brand"></a>
                </div>
                <div class="single_brand_item">
                  <a href="#"><img v-lazy-load  data-src="/assets/images/resources/brand-1-4.png" alt="brand"></a>
                </div>
                <div class="single_brand_item">
                  <a href="#"><img v-lazy-load  data-src="/assets/images/resources/brand-1-5.png" alt="brand"></a>
                </div>
              </carousel>
            </client-only>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
    export default {
        name: "BrandFour"
    }
</script>

<style scoped>

</style>
