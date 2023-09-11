<template>
  <div>
    <LazyPageHeader title="Services" />
    <section class="service_one">
      <div class="container">
        <div class="block-title text-center">
          <p>What we do</p>
          <h3>Services We Offer</h3>
          <div class="leaf">
            <img v-lazy-load data-src="/assets/images/resources/leaf.png" alt="" />
          </div>
        </div>
        <content-placeholders
          class="position-relative border-radius-10 placeholders"
          v-show="services.length == 0"
          rounded
        >
          <div class="row">
            <div class="col-xl-3 col-lg-3 col-md-6">
              <content-placeholders-heading :lines="1"/><content-placeholders-img />
            </div>
            <div class="col-xl-3 col-lg-3 col-md-6">
              <content-placeholders-heading :lines="1"/><content-placeholders-img />
            </div>
            <div class="col-xl-3 col-lg-3 col-md-6">
              <content-placeholders-heading :lines="1"/><content-placeholders-img />
            </div>
            <div class="col-xl-3 col-lg-3 col-md-6">
              <content-placeholders-heading :lines="1"/><content-placeholders-img />
            </div>
          </div>
        </content-placeholders>
        <div class="row" v-if="services">
          <div
            class="col-xl-3 col-lg-3 col-md-6"
            v-for="service in services.data"
            :key="service.id"
          >
            <div class="service_1_single wow fadeInUp">
              <div class="content">
                <h3>{{ service.name }}</h3>
                <p>{{ service.summary }}</p>
              </div>
              <div class="service_1_img">
                <img v-lazy-load :src="service.media_url" :alt="service.media[0].name" />
                <div class="hover_box">
                  <nuxt-link :to="service.slug=='shipping'?'/shipping':'/services/' + service.slug"
                    ><span class="icon-left-arrow"></span
                  ></nuxt-link>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="row">
          <div class="col-xl-12" v-if="this.services">
            <div class="our_projects_btn" v-if="this.services.last_page >  this.currentPage">
              <a @click="loadMore" class="thm-btn" style="cursor: pointer;">Load More Services</a>
            </div>
          </div>
        </div>
      </div>
    </section>



  </div>
</template>

<script>

export default {
  async fetch() {
    const responsePage = await this.$api.fetchServices(this.currentPage);
    this.services = responsePage.services;
  },

  data() {
    return {
      currentPage:1,
      services: [],
    };
  },
  head() {
    return {
      title: "Agroethical | Services",
    };
  },
  methods:{
   async loadMore(){
      if(this.services.last_page >  this.currentPage){
        this.currentPage = this.services.current_page +1
        const responsePage = await this.$api.fetchServices(this.currentPage)
        this.services.data = [...this.services.data,...responsePage.services.data]
      }
    }
  },

};
</script>

<style scoped>
.ac {
  margin-top: 10px;
  padding: 10px;
  background: #ffffff;
  box-sizing: border-box;
}

.ac > .ac-q {
  font-size: 20px;
  color: #444;
  padding: 10px 30px 10px 10px;
  margin: 0;
  text-decoration: none;
  display: block;
  cursor: pointer;
  position: relative;
  font-weight: 400;
  font-family: var(--heading-font);
}

.ac.is-active .ac-q {
  color: #5a8b50 !important;
}
.ac > .ac-q::after {
  content: "+";
  text-align: center;
  width: 15px;
  right: 10px;
  top: 50%;
  -webkit-transform: translate(0, -50%);
  transform: translate(0, -50%);
  position: absolute;
}

.ac > .ac-a {
  overflow: hidden;
  -webkit-transition-property: all;
  transition-property: all;
  -webkit-transition-timing-function: ease;
  transition-timing-function: ease;
}

.ac > .ac-a p {
  color: #878e9c;
  margin: 0;
  padding: 10px;
  font-size: 16px;
  font-weight: 400;
}

.ac.js-enabled > .ac-a {
  visibility: hidden;
}

.ac.is-active > .ac-a {
  visibility: visible;
}

.ac.is-active > .ac-q::after {
  content: "\2013";
  color: #5a8b50;
}
</style>
