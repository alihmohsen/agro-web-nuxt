<template>
  <section class="welcome_one">
    <div class="container">
      <div class="row">
        <div class="col-xl-12 col-lg-12">
          <div class="block-title text-center">
            <p>Welcome to Agroethical</p>
            <h3>Who are we?</h3>
            <div class="leaf text-center">
              <img v-lazy-load data-src="/assets/images/resources/leaf.png" alt="leaf">
            </div>
          </div>
        </div>

        <div class="col-xl-6 col-lg-6">
          <div class="growing_box py-2">
            <div class="growing_icon_box">
              <img v-lazy-load style="width:130px" data-src="/assets/images/cow.svg" alt="cow">
            </div>
            <div class="growing_text text-center text-lg-left">
              <p>Professional expertise at your hands! </p>
              <nuxt-link to="/about" class="mt-3 px-3 px-lg-5 py-2 thm-btn contact-one__btn" style="cursor: pointer;">Read More</nuxt-link>
            </div>
          </div>
        </div>

        <div class="col-xl-6 col-lg-6">
          <div class="welcome_text">
            <p>Agroethical is a leading supplier of a variety of cattle and livestock products. At Agroethical, our main
              concern is customer satisfaction, with unwavering commitment to quality of provided service and products.
            </p>
          </div>
          <!-- <div class="welcome_video_box" style="background-image:url(/assets/images/resources/welcome_video_bg.jpg)">
            <a href="https://www.youtube.com/watch?v=i9E_Blai8vk" class="welcome_video_btn videoTwo"><i
                class="fa fa-play"></i></a>
          </div> -->
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "WelcomeOne",
  mounted() {
    new GLightbox({
      selector: '.videoTwo',
      touchNavigation: true,
      loop: true,
      autoplayVideos: true
    });
  }
}
</script>

<style scoped>

</style>
