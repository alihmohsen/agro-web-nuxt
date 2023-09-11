<template>
  <div>
    <LazyPageHeader :title="product.name" />

    <section class="product_detail mb-4">
      <div class="container">
        <div class="row">
          <div class="col-xl-6">
            <div class="product-tab-box tabs-box">
              <div class="mission-tabs">
                <!--Tab-->
                <input type="radio" name="tabs" id="tab-one" checked="checked" />
                <label for="tab-one" class="tab-btn">Description</label>
                <div class="tab">
                  <div class="active-tab">
                    <div class="content">
                      <div class="product-details-content">
                        <h1>
                          {{ product.name }}
                        </h1>
                        <div class="desc-content-box">
                          <div v-html="product.description"></div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <div class="col-xl-6">
            <div class="gallery-contain">
              <div class="item" v-for="(photo, i) in product.gallery" :key="i">
                <div class="gallery_two_single">
                  <a :href="photo" data-fancybox="image" data-caption="" >
                    <img
                      class="rounded w-100"
                      v-lazy-load
                      :data-src="photo"
                      alt=""
                    />
                  </a>
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
  name: "ProductDetail",
  head() {
    return {
      title: `agroethical | ${this.product.name}`,
      meta: [
        {
          hid: "description",
          name: "description",
          content: this.product.summary,
        },
      ],
    };
  },

  data() {
    return {
      related_products: [],
    };
  },

  asyncData(context) {
    return context.$api
      .fetchSingleProduct(context.params.slug)
      .then((response) => {
        return {
          product: response.product[0],
        };
      })
      .catch((e) => context.error(e));
  },

  methods: {
    async RelatedProducts(id) {
      const responsePage = await this.$api.fetchProductsByCategories(id)
      this.related_products = responsePage.products
    },
  },
  created() {
    this.RelatedProducts(this.product.categories[0].id)
  },
};
</script>

<style scoped>
.mission-tabs {
  display: flex;
  flex-wrap: wrap;
}

.mission-tabs label {
  order: 1;
  display: block;
  padding: 17px 50px;
  margin-right: 0.2rem;
  cursor: pointer;
  background: #5e9054;
  font-weight: 500;
  transition: background ease 0.2s;
  font-size: 19px;
  text-transform: uppercase;
  color: #fff;
}

.mission-tabs .tab {
  order: 99;
  flex-grow: 1;
  width: 100%;
  display: none;
  padding: 1rem;
  background: #f4f5f8;
}

.default-tabs .mission-tabs .text {
  position: relative;
  font-size: 20px;
  font-weight: 300;
  color: #5e9054;
  line-height: 1.7em;
  letter-spacing: 2px;
}

.mission-tabs input[type="radio"] {
  display: none;
}

.mission-tabs input[type="radio"]:checked+label {
  background: #f4f5f8;
  color: #222;
}

.mission-tabs input[type="radio"]:checked+label+.tab {
  display: block;
}

@media (max-width: 45em) {

  .mission-tabs .tab,
  .mission-tabs label {
    order: initial;
  }

  .mission-tabs label {
    width: 100%;
    margin-right: 0;
    margin-top: 0.2rem;
  }
}
</style>
