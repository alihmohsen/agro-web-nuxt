<template>
  <section class="gallery_two">
    <div class="container">
      <content-placeholders
          class="position-relative border-radius-10 placeholders"
          v-show="gallery.meta.length == 0"
          rounded
        >
          <div class="row">
            <div class="col-xl-4 col-lg-4 col-md-6">
              <content-placeholders-img />
            </div>
            <div class="col-xl-4 col-lg-4 col-md-6">
              <content-placeholders-img />
            </div>
            <div class="col-xl-4 col-lg-4 col-md-6">
              <content-placeholders-img />
            </div>

          </div>
        </content-placeholders>
      <div class="gallery-contain">
       
        <div class="item" v-for="(photo, i) in gallery.data" :key="i">
          <div class="gallery_two_single">
            <div class="gallery_two_image">
              <img class="rounded" v-lazy-load :data-src="photo" alt="" style="width: 100%" />
              <div class="gallery_two_hover_box">
                <div class="gallery_two_icon">
                  <a class="img-popup" :href="photo" data-fancybox="image" data-caption="">
                    <span><i class="fas fa-eye"></i></span></a>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="row text-center">
      <div class="col-xl-12" v-if="this.gallery">
        <div class="our_projects_btn" v-if="this.gallery.meta.last_page > this.currentPage">
          <button @click="loadMore" class="thm-btn" style="cursor: pointer;">Load More Images</button>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "Gallery",
  data() {
    return {
      gallery: {
        meta: []
      },
      currentPage: 1,
    };
  },
  async fetch() {
    const responseGallery = await this.$api.fetchGallery();
    this.gallery = responseGallery;
  },
  methods: {
    async loadMore() {
      if (this.gallery.meta.last_page > this.currentPage) {
        this.currentPage = this.gallery.meta.current_page + 1
        const responsePage = await this.$api.fetchGallery(this.currentPage)
        this.gallery.data = [...this.gallery.data, ...responsePage.data]
      }
    }
  },
  mounted() {
    new GLightbox({
      selector: ".img-popup",
    });
  },
};
</script>

<style scoped>
@media (max-width: 1214px) {
  .masonary-item {
    position: static !important;
    display: block;
  }

  .masonary-layout {
    position: static !important;
    height: 100% !important;
  }
}
</style>
