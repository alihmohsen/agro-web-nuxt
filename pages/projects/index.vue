<template>
  <div>
    <LazyPageHeader title="Our Projects" />
        <div class="block-title text-center mt-5">
          <p>explore projects</p>
          <h3>our Recent projects</h3>
          <div class="leaf">
            <img v-lazy-load  data-src="/assets/images/resources/leaf.png" alt="">
          </div>
        </div>
    <section class="recent-project our_projects" >
      <div class="container">
        <div class="row" v-if="projects">
          <div
            class="col-xl-4 col-lg-4"
            v-for="project in projects.data"
            :key="project.id"
          >
            <div class="recent_project_single mrb-30">
              <div class="project_img_box">
                <img v-lazy-load  :data-src="project.media_url" :alt="project.media[0].name" />
                <div class="project_content">
                  <h3>{{ project.name }}</h3>
                  <p>{{ project.summary }}</p>

                </div>
                <div class="hover_box">
                  <nuxt-link :to="'/projects/'+project.slug"
                    ><span class="icon-left-arrow text-white"></span
                  ></nuxt-link>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="row">
          <div class="col-xl-12" v-if="this.projects">
            <div class="our_projects_btn" v-if="this.projects.last_page >  this.currentPage">
              <button @click="loadMore" class="thm-btn" style="cursor: pointer;">Load More Projects</button>
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
    const responsePage = await this.$api.fetchProjects();
    this.projects = responsePage.projects;
  },
  data() {
    return {
      currentPage:1,
      projects: null,
    };
  },
  head() {
    return {
      title: "Agroethical | Projects",
    };
  },
  methods:{
   async loadMore(){
      if(this.projects.last_page >  this.currentPage){
        this.currentPage = this.projects.current_page +1
        const responsePage = await this.$api.fetchProjects(this.currentPage)
        this.projects.data = [...this.projects.data,...responsePage.projects.data]
      }
    }
  },

};
</script>
