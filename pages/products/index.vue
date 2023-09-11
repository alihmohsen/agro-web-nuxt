<template>
  <div>
    <LazyPageHeader title="Product Categories" />

    <section class="product">
      <div class="container">
        <content-placeholders
          class="position-relative border-radius-10 placeholders"
          v-show="categories.length == 0"
          rounded
        >
          <div class="row">
            <div class="col-xl-4 col-lg-4 col-md-6">
              <content-placeholders-img /> <content-placeholders-heading />
            </div>
            <div class="col-xl-4 col-lg-4 col-md-6">
              <content-placeholders-img /> <content-placeholders-heading />
            </div>
            <div class="col-xl-4 col-lg-4 col-md-6">
              <content-placeholders-img /> <content-placeholders-heading />
            </div>
          </div>
        </content-placeholders>
        <div class="row" v-if="categories">
          <div
            class="col-xl-4 col-lg-4 col-md-6"
            v-for="category in categories"
            :key="category.id"
          >
            <div class="all_products_single text-center">
              <div class="all_product_item_image">
                <img v-lazy-load :data-src="category.media_url" alt="" />
                <div class="all_product_hover">
                  <div class="all_product_icon">
                    <nuxt-link :to="'/products/category/' + category.slug">
                      <span class="">
                        <i class="far fa-eye text-white"></i>
                      </span>
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
      categories: [],
    };
  },
  async fetch() {
    const responseCategories = await this.$api.fetchCategories();
    this.categories = responseCategories.category;
  },
};
</script>

