<template>
  <div>
    <LazySliderThree />
    <LazyWelcomeOne />

    <section class="service_three">
      <div class="container">
        <div class="row">
          <div class="col-12 d-flex justify-content-center">
            <div class="block-title text-center">
              <p>explore Services</p>
              <h3>Our Services</h3>
              <div class="leaf text-center">
                <img
                  v-lazy-load
                  data-src="/assets/images/resources/leaf.png"
                  alt="leaf"
                />
              </div>
            </div>
          </div>
          <content-placeholders
            class="position-relative border-radius-10 placeholders col-12"
            v-show="services.length == 0"
            rounded
          >
            <div class="row">
              <div class="col-xl-3 col-lg-3 col-md-6">
                <content-placeholders-img /><content-placeholders-heading
                  :lines="1"
                />
              </div>
              <div class="col-xl-3 col-lg-3 col-md-6">
                <content-placeholders-img /><content-placeholders-heading
                  :lines="1"
                />
              </div>
              <div class="col-xl-3 col-lg-3 col-md-6">
                <content-placeholders-img /><content-placeholders-heading
                  :lines="1"
                />
              </div>
              <div class="col-xl-3 col-lg-3 col-md-6">
                <content-placeholders-img /><content-placeholders-heading
                  :lines="1"
                />
              </div>
            </div>
          </content-placeholders>
          <div
            class="col-xl-3 col-lg-3 col-md-6"
            v-for="(service, index) in services.data"
            :key="service.id"
          >
            <div
              v-if="index < 4"
              class="service_three_single wow fadeInLeft"
              data-wow-delay="300ms"
            >
              <div class="service_three_image">
                <img
                  v-lazy-load
                  :data-src="service.media_url"
                  :alt="service.media[0].name"
                />
              </div>
              <div class="service_three_content">
                <h2>
                  <nuxt-link
                    :to="
                      service.slug == 'shipping'
                        ? '/shipping'
                        : '/services/' + service.slug
                    "
                    >{{ service.name }}</nuxt-link
                  >
                </h2>
                <p>{{ service.summary }}</p>
                <div class="service_three_read_more">
                  <nuxt-link
                    :to="
                      service.slug == 'shipping'
                        ? '/shipping'
                        : '/services/' + service.slug
                    "
                    ><i class="fa fa-angle-right"></i>Read More</nuxt-link
                  >
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <section class="recent_project_three">
      <div class="container">
        <div class="block-title text-center">
          <p>explore Products</p>
          <h3>our Products</h3>
          <div class="leaf">
            <img
              v-lazy-load
              data-src="/assets/images/resources/leaf.png"
              alt=""
            />
          </div>
        </div>
        <content-placeholders
          class="position-relative border-radius-10 placeholders"
          v-show="categories.length == 0"
          rounded
        >
          <div class="row">
            <div class="col-xl-3 col-lg-3 col-md-6">
              <content-placeholders-img /><content-placeholders-heading
                :lines="1"
              />
            </div>
            <div class="col-xl-3 col-lg-3 col-md-6">
              <content-placeholders-img /><content-placeholders-heading
                :lines="1"
              />
            </div>
            <div class="col-xl-3 col-lg-3 col-md-6">
              <content-placeholders-img /><content-placeholders-heading
                :lines="1"
              />
            </div>
            <div class="col-xl-3 col-lg-3 col-md-6">
              <content-placeholders-img /><content-placeholders-heading
                :lines="1"
              />
            </div>
          </div>
        </content-placeholders>
        <div class="all_products" v-if="categories.length > 0">
          <client-only>
            <carousel
              :autoplay="false"
              :responsive="{
                0: { items: 1 },
                576: { items: 2 },
                992: { items: 3 },
              }"
              :nav="false"
            >
              <div
                class="slide-item"
                v-for="category in categories"
                :key="category.id"
              >
                <div class="all_products_single text-center px-1">
                  <div class="all_product_item_image">
                    <img :src="category.media_url" :alt="category.name" />
                    <div class="all_product_hover">
                      <div class="all_product_icon">
                        <nuxt-link :to="'/products/category/' + category.slug"
                          ><span class=""
                            ><i class="far fa-eye text-white"></i
                          ></span>
                        </nuxt-link>
                      </div>
                    </div>
                  </div>

                  <h4>
                    <nuxt-link :to="'/products/category/' + category.slug">{{
                      category.name
                    }}</nuxt-link>
                  </h4>
                </div>
              </div>
            </carousel>
          </client-only>
        </div>
      </div>
    </section>

    <LazyQuoteOne />
    <LazyWhyChooseOne />
    <LazyWorkOne />
    <LazyWhatMakes />
    <LazyGMap />
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: "Agroethical  | Home",
    };
  },
  async fetch() {
    const responseCategories = await this.$api.fetchCategories();
    this.categories = responseCategories.category;

    const responseService = await this.$api.fetchServices();
    this.services = responseService.services;
  },

  data() {
    return {
      currentPage: 1,
      blogs: null,
      projects: [],
      services: [],
      categories: [],
    };
  },
};
</script>
