<template>
  <div class="site_header__header_three_wrap">
    <div class="topbar-three">
      <div class="container-box">
        <div class="topbar_three_content clearfix">
          <div class="logo-box-three float-left">
            <nuxt-link to="/" class="main-nag__logo">
              <img v-lazy-load  data-src="/assets/images/resources/logo-2.png" width="85" alt="" />
            </nuxt-link>
          </div>

          <div class="topbar_three_nav_box float-left">
            <nav class="header-navigation stricky clearfix">
              <div class="container">
                <div class="main_nav_header_three_content clearfix">
                  <div class="mobile_menu_icon_three">
                    <div class="side-menu__toggler">
                      <i @click="mobileToggle = !mobileToggle" class="fa fa-bars"></i>
                    </div>
                  </div>
                  <div class="main-nav__main-navigation three float-left">
                    <ul class="main-nav__navigation-box">
                      <li v-for="link, index in links" :key="index" class="dropdown"  style="cursor: pointer;"
                        :class="link.path == getLocation ? 'current' : ''">
                        <a @click="goTo(link.path)"  >{{ link.name }}</a>
                      </li>
                    </ul>
                  </div>

                  <!-- <div class="main_nav_right_three float-right">
                    <div class="icon_search_box">
                      <a
                        href="#"
                        class="main-nav__search search-popup__toggler"
                        @click="searchPopupStatusChange"
                        ><i class="icon-magnifying-glass"></i
                      ></a>
                    </div>
                  </div> -->
                </div>
              </div>
            </nav>
          </div>

          <div class="topbar_three_right_box">
            <div class="topbar-one__social home-four">
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

    <nav class="mobile-nav__container" :style="`display: ${mobileToggle ? 'block' : 'none'}`">
      <ul class="main-nav__navigation-box">
        <li v-for="link, index in links" :key="index" class="dropdown " style="cursor: pointer;"
          :class="link.path == getLocation ? 'current' : ''">
          <a @click="goTo(link.path)" >{{ link.name }}</a>
        </li>
      </ul>
    </nav>
  </div>
</template>

<script>
import { mapMutations } from "vuex";
export default {
  name: "Nav",
  props: {
    social: Object,
  },
  data() {
    return {
      mobileToggle: false,
      windowHeight: null,
      links: [
        // { name: "Home", path: "/" },
        { name: "About Us", path: "/about" },
        { name: "Services", path: "/services" },
        // { name: "Our Project", path: "/projects" },
        { name: "Shipping", path: "/shipping" },
        // { name: "Categories", path: "/categories" },
        { name: "Products", path: "/products" },
        { name: "Gallery", path: "/gallery" },
        // { name: "News", path: "/news" },
        { name: "Contact", path: "/contact" },
      ],
    };
  },
  computed: {
    searchPopup() {
      return this.$store.state.searchPopupStatus;
    },
    getLocation() {
      return this.$route.path;
    },
  },
  mounted() {
    window.addEventListener('resize', this.onResize);
  },
  methods: {
    onResize() {
      this.windowWidth = window.innerWidth
      if(window.innerWidth>=1200){
        this.mobileToggle = false;
      }
    },
    goTo(route) {
      this.mobileToggle =false
      this.$router.push(route);
    },
    ...mapMutations({
      searchPopupStatusChange: "changeSearchPopupStatus",
    }),
  },
};
</script>