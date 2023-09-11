<template>
  <div>
    <LazyPageHeader title="News" />

    <section class="news_detail">
      <div class="container">
        <div class="row">
          <div class="col-xl-12 col-lg-12" v-if="blog">
            <div class="news_detail_left">
              <div class="news_detail_image_box">
                <img
                  v-lazy-load
                  :data-src="blog.media_url"
                  :alt="blog.media[0].name"
                />
                <div class="news_detail_date_box">
                  <p>{{ blog.created_at }}</p>
                </div>
              </div>

              <div class="news_detail_content mt-5">
                <h2>{{ blog.title }}</h2>
                <div
                  class="news_detail_one_text"
                  v-html="blog.description"
                ></div>
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
  data() {
    return {
      // page:{}
      blog: null,
    };
  },

  head() {
    return {
      title: `agroethical | ${this.blog.title}`,
      meta: [
        {
          hid: "description",
          name: "description",
          content: this.blog.summary,
        },
      ],
    };
  },

  asyncData(context) {
    return context.$api
      .fetchSingleBlog(context.params.slug)
      .then((response) => {
        return {
          blog: response.blog,
        };
      })
      .catch((e) => context.error(e));
  },
};
</script>
