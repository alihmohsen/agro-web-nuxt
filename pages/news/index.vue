<template>
  <div>
    <LazyPageHeader title="News" />
    <section class="blog-one news">
      <div class="container">
        <div class="row" v-if="blogs">
          <div class="col-xl-4 col-lg-4" v-for="blog in blogs.data" :key="blog.id">
            <div class="blog_one_single mb-30">
              <div class="blog_one_image">
                <div class="blog_image">
                  <img v-lazy-load  :data-src="blog.media_url" :alt="blog.media[0].name">
                  <div class="blog_one_date_box">
                    <p>{{blog.created_at}}</p>
                  </div>
                </div>
                <div class="blog-one__content">
                  <h3>
                    <nuxt-link :to="'/news/'+blog.slug">{{blog.title}}</nuxt-link>
                  </h3>
                  <div class="blog_one_text">
                    <p>{{blog.summary}}</p>
                  </div>
                  <div class="read_more_btn">
                    <nuxt-link :to="'/news/'+blog.slug"><i class="fa fa-angle-right"></i>Read More</nuxt-link>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="row">
          <div class="col-xl-12" v-if="this.blogs">
            <div class="our_projects_btn" v-if="this.blogs.last_page >  this.currentPage">
              <button @click="loadMore" class="thm-btn" style="cursor: pointer;">Load More News</button>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      blogs: {},
      currentPage:1
    }
  },

  head() {
    return {
      title: "Agroethical  | News"
    }
  },
  async fetch() {
    const responsePage = await this.$api.fetchBlog(this.currentPage)
    this.blogs = responsePage.blogs
  },
  methods:{
   async loadMore(){
      if(this.blogs.last_page >  this.currentPage){
        this.currentPage = this.blogs.current_page +1
        const responsePage = await this.$api.fetchBlog(this.currentPage)
        this.blogs.data = [...this.blogs.data,...responsePage.blogs.data]
      }
    }
  },
}
</script>
