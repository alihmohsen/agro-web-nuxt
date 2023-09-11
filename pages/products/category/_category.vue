<template>
  <div>
    <section class="page-header" style="background-image: url(/assets/images/backgrounds/page-header-contact.jpeg);">
      <div class="container">
        <h2 v-if="categories.length>0">{{categories[activeCategory].name}}</h2>
        <ul class="thm-breadcrumb list-unstyled">
          <li><nuxt-link to="/">Home</nuxt-link></li>
          <li><span v-if="categories.length>0">{{categories[activeCategory].name}}</span></li>
        </ul>
      </div>
    </section>

    <section class="product">
      <div class="container">
        <div class="row">
          <div class="col-xl-4 col-lg-3 col-md-6">
            <div class="sidebar-wrapper style2">
              <div class="single-sidebar wow fadeInUp animated animated" data-wow-delay="0.3s"
                data-wow-duration="1200ms" style="visibility: visible;animation-duration: 1200ms;
                animation-delay: 0.3s;
                  animation-name: fadeInUp;
                ">
                <div class="categories-box">
                  <div class="title">
                    <h3>Categories</h3>
                  </div>
                  <ul class="categories clearfix">
                    <li v-for="(category, i) in categories" :key="i"
                      :class="{ 'active-category': currentCategoryId == category.slug }">
                      <nuxt-link :to="'/products/category/' + category.slug">
                        {{ category.name }}
                      </nuxt-link>
                    </li>
                  </ul>
                </div>
              </div>
            </div>
          </div>
          <!--End Sidebar Wrapper-->
          <div class="col-xl-8 col-lg-9">
            <div class="product-items">
             
              <content-placeholders
          class="position-relative border-radius-10 placeholders"
          v-show="products.length == 0"
          rounded
        >
          <div class="row">
            <div class="col-xl-3 col-lg-3 col-md-6">
              <content-placeholders-img /><content-placeholders-heading :lines="1"/>
            </div>
            <div class="col-xl-3 col-lg-3 col-md-6">
              <content-placeholders-img /><content-placeholders-heading :lines="1"/>
            </div>
            <div class="col-xl-3 col-lg-3 col-md-6">
              <content-placeholders-img /><content-placeholders-heading :lines="1"/>
            </div>
            <div class="col-xl-3 col-lg-3 col-md-6">
              <content-placeholders-img /><content-placeholders-heading :lines="1"/>
            </div>
          </div>
        </content-placeholders>
              <div class="all_products" v-if="products.data">
                <div class="row">
                  <div class="col-xl-4 col-lg-4 col-md-6" v-for="product in products.data" :key="product.id">
                    <div class="all_products_single text-center">
                      <div class="all_product_item_image">
                        <div class="product_image">
                          <img v-lazy-load :data-src="product.media_url" alt="" />
                        </div>
                        <div class="all_product_hover">
                          <div class="all_product_icon">
                            <nuxt-link :to="'/products/' + product.slug">
                              <span class="">
                                <i class="far fa-eye text-white"></i>
                              </span>
                            </nuxt-link>
                          </div>
                        </div>
                      </div>

                      <h4>
                        <nuxt-link :to="'/products/' + product.slug">{{
                            product.name
                        }}</nuxt-link>
                      </h4>
                      <!-- <p>${{ product.price }}</p> -->
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: "Agroethical  | Products",
    };
  },

  data() {
    return {
      products: [],
      categories: [],
      activeCategory: 1,
    };
  },
  asyncData(context) {
    return context.$api
      .fetchProductsByCategories(context.params.category)
      .then((response) => {
        return {
          currentCategoryId: context.params.category,
          products: response.products,
        };
      })
      .catch((e) => context.error(e));
  },

  async fetch() {
    const responseCategories = await this.$api.fetchCategories();
    this.categories = responseCategories.category;
    this.activeCategory = this.categories.findIndex(x=>x.slug == this.currentCategoryId)
  },

  methods: {

  },
};
</script>
<style >
.active-category a {
  color: green !important;
}
</style>
