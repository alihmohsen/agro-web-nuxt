<template>
  <div>
    <footer class="site-footer">
      <div class="site-footer_farm_image"><img v-lazy-load  data-src="/assets/images/resources/site-footer-farm.png" alt="Farm Image">
      </div>
      <div class="container">
        <div class="row no-gutters">
          <div class="col-xl-4 col-lg-6 col-md-6">
            <div class="footer-widget__column footer-widget__about wow fadeInUp" data-wow-delay="100ms">
              <div class="footer-widget__title">
                <h3>About</h3>
              </div>
              <div class="footer-widget_about_text">
                <p>Agroethical is a leading supplier of a variety of cattle and livestock products. At Agroethical, our
                  main concern is customer satisfaction, with unwavering commitment to quality of provided service and
                  products. </p>
              </div>
              <!-- <form>
                  <div class="footer_input-box">
                    <input type="Email" placeholder="Email Address">
                    <button type="submit" class="button"><i class="fa fa-check"></i></button>
                  </div>
                </form> -->
            </div>
          </div>
          <div class="col-xl-4 col-lg-6 col-md-6">
            <div class="footer-widget__column footer-widget__link wow fadeInUp" data-wow-delay="200ms">
              <div class="footer-widget__title">
                <h3>Explore</h3>
              </div>
              <ul class="footer-widget__links-list list-unstyled">
                <li v-for="link,index in links" :key="index">
                  <nuxt-link :to="link.path">{{ link.name }}</nuxt-link>
                </li>
              </ul>
            </div>
          </div>
          <!-- <div class="col-xl-3 col-lg-3 col-md-6">
              <div class="footer-widget__column footer-widget__news wow fadeInUp" data-wow-delay="300ms">
                <div class="footer-widget__title">
                  <h3>News</h3>
                </div>
                <ul class="footer-widget__news list-unstyled">
                  <li>
                    <div class="footer-widget__news_image">
                      <img v-lazy-load  data-src="/assets/images/resources/footer-1-img-1.jpg" alt="">
                    </div>
                    <div class="footer-widget__news_text">
                      <p><a href="/news_detail"> Learn 10 Best Tips for New Formers</a></p>
                    </div>
                    <div class="footer-widget__news_date_box">
                      <p>30 Oct, 2020</p>
                    </div>
                  </li>
                  <li>
                    <div class="footer-widget__news_image">
                      <img v-lazy-load  data-src="/assets/images/resources/footer-1-img-2.jpg" alt="">
                    </div>
                    <div class="footer-widget__news_text">
                      <p><a href="/news_detail">Farmer Sentiment Darkens Hopes Fade</a></p>
                    </div>
                    <div class="footer-widget__news_date_box">
                      <p>30 Oct, 2020</p>
                    </div>
                  </li>
                </ul>
              </div>
            </div> -->
          <div class="col-xl-4 col-lg-6 col-md-6">
            <div class="footer-widget__column footer-widget__contact wow fadeInUp" data-wow-delay="400ms">
              <div class="footer-widget__title">
                <h3>Contact</h3>
              </div>
              <div class="footer-widget_contact">
                <p>AgroEthical s.r.o
                  <br>Racianska 88B, 83102 Bratislava, Slovakia
                </p>
                <a href="mailto:contact@agroethical.com"><i class="far fa-envelope"></i>  contact@agroethical.com</a><br>
                <a href="tel:+33605766548"><i  class="fas fa-phone"></i> +33 6 05 76 65 48</a>
                <div class="site-footer__social">
                  <a target="_blank" :href="social.facebook" v-if="social.facebook" ><i class="fab fa-facebook-square"></i></a>
                  <!-- <a target="_blank" :href="social.twitter" v-if="social.twitter" ><i class="fab fa-twitter"></i></a> -->
                  <a target="_blank" :href="social.instagram" v-if="social.instagram" ><i class="fab fa-instagram"></i></a>
                  <!-- <a target="_blank" :href="social.tiktok" v-if="social.tiktok" >
                    <svg width="10" fill="#878986" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512">
                      <path d="M448,209.91a210.06,210.06,0,0,1-122.77-39.25V349.38A162.55,162.55,0,1,1,185,188.31V278.2a74.62,74.62,0,1,0,52.23,71.18V0l88,0a121.18,121.18,0,0,0,1.86,22.17h0A122.18,122.18,0,0,0,381,102.39a121.43,121.43,0,0,0,67,20.14Z" />
                    </svg>
                  </a> -->
                  <!-- <a target="_blank" :href="social.linkedin" v-if="social.linkedin" ><i class="fab fa-linkedin"></i></a> -->
                  <!-- <a target="_blank" :href="social.youtube" v-if="social.youtube" ><i class="fab fa-youtube"></i></a> -->
                  <a target="_blank" :href="social.whatsapp" v-if="social.whatsapp" ><i class="fab fa-whatsapp"></i></a>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </footer>

    <div class="site-footer_bottom">
      <div class="container">
        <div class="site-footer_bottom_copyright">
          <p>All Rights Reserved for AGROETHICAL © 2022 ,<span class="mx-2">Developed by Consigliere</span></p>
        </div>
        <!-- <div class="site-footer_bottom_menu">
            <ul class="list-unstyled">
              <li><a href="#">Privacy Policy</a></li>
              <li><a href="#">Terms of Use</a></li>
            </ul>
          </div> -->
      </div>
    </div>

    <a @click="scrollTop" href="#" class="scroll-to-target scroll-to-top"
      :style="`display: ${scrollBtn ? 'block' : 'none'}`"><i class="fa fa-angle-up"></i></a>

  </div>
</template>

<script>
export default {
  name: "Footer",
  props: {
    social: Object
  },
  data() {
    return {
      links: [
        { name: "Home", path: "/" },
        { name: "Services", path: "/services" },
        { name: "Products", path: "/products" },
        // { name: "Our Project", path: "/projects" },
        { name: "Shipping", path: "/shipping" },
        { name: "Gallery", path: "/gallery" },
        // { name: "News", path: "/news" },
        { name: "Contact", path: "/contact" },
      ],
      scrollBtn: false
    }
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
  },

  methods: {

    handleScroll() {

      if (window.scrollY > 70) {
        this.scrollBtn = true
      }
      else if (window.scrollY < 70) {
        this.scrollBtn = false
      }
    },

    scrollTop() {
      window.scrollTo(0, 0);
    }

  }
}
</script>


