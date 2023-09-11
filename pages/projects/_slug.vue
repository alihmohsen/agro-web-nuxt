<template>
  <div>
    <section
      class="page-header"
      :style="'background-image: url(' + project.media_url + ');'"
    >
      <div class="container">
        <h2>{{ project.name }}</h2>
        <ul class="thm-breadcrumb list-unstyled">
          <li><nuxt-link to="/">Home</nuxt-link></li>
          <li>
            <span>{{ project.name }}</span>
          </li>
        </ul>
      </div>
    </section>
    <section class="project_detail">
      <div class="container" v-if="project">
        <div class="row">
          <div class="col-xl-12 col-lg-12 col-md-12">
            <div class="project_detail_image">
              <img
                v-lazy-load
                :data-src="project.media_url"
                :alt="project.media.name"
              />
            </div>
          </div>
        </div>
        <div class="row">
          <div class="col-xl-12 col-lg-12">
            <div class="project_detail_left_content">
              <div class="harvest_innovations_detail">
                <h2>{{ project.name }}</h2>
                <div v-html="project.description"></div>
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
      title: `agroethical | ${this.project.name}`,
      meta: [
        {
          hid: "description",
          name: "description",
          content: this.project.summary,
        },
      ],
    };
  },
  asyncData(context) {
    return context.$api
      .fetchSingleProjects(context.params.slug)
      .then((response) => {
        return {
          project: response.project,
        };
      })
      .catch((e) => context.error(e));
  },
};
</script>
