<template>
  <div>
    <LazyPageHeader title="service" />

    <section class="service_detail">
      <div class="container">
        <div class="row">
          <!-- <div class="col-xl-4 col-lg-4">
          <div class="service_details_left">
            <ul class="list-unstyled service_all_list">
              <li><a href="#">All Services</a></li>
              <li class="active"><a href="#">Fresh Vegetables</a></li>
              <li><a href="#">Agriculture Products</a></li>
              <li><a href="#">Organic Products</a></li>
              <li><a href="#">Dairy Products</a></li>
            </ul>
            <div class="need_help_box">
              <h2>Need Help?</h2>
              <p>Speak with a human to filling out a form? call corporate office and we will connect
                you with a team member who can help.</p>
              <h3><span class="icon-phone-call"></span>666 888 0000</h3>
            </div>
            <div class="download_file_box">
              <a href="#"><i class="icon-pdf"></i>Download PDF File</a>
            </div>
          </div>
        </div> -->
          <div class="col-xl-12 col-lg-12">
            <div class="service_details_right">
              <div class="service_details_One_img">
                <img v-lazy-load :data-src="service.media_url" :alt="service.media[0].name">
              </div>
              <div class="harvest_innovations">
                <h2>{{ service.name }}</h2>
                <div v-html="service.description"></div>
              </div>
              <!-- <div class="row">
              <div class="col-xl-6 col-lg-6">
                <div class="service_details_single_img_box">
                  <img v-lazy-load data-src="/assets/images/service/service-detail_img_2.jpg" alt="">
                </div>
              </div>
              <div class="col-xl-6 col-lg-6">
                <div class="service_details_single_img_box">
                  <img v-lazy-load data-src="/assets/images/service/service-detail_img_3.jpg" alt="">
                </div>
              </div>
            </div>
            <div class="agriculture_solutions">
              <h3>Agriculture Solutions</h3>
              <p>Lorem ipsum is simply free text used by copytyping refreshing. Neque porro est qui
                dolorem ipsum quia quaed inventore veritatis et quasi architecto beatae vitae dicta
                sunt explicabo. Aelltes port lacus quis enim var sed efficitur turpis gilla sed sit
                amet finibus eros. Lorem Ipsum is simply dummy text of the printing and typesetting
                industry.</p>
            </div>
            <ul class="list-unstyled">
              <li><i class="fa fa-check"></i>Research beyond the business plan</li>
              <li><i class="fa fa-check"></i>Marketing options and rates</li>
              <li><i class="fa fa-check"></i>The ability to turnaround consulting</li>
              <li><i class="fa fa-check"></i>Help companies into more profitable</li>
            </ul>
            <p class="service_details_last_text">Lorem Ipsum has been the ndustry standard dummy text
              ever since the 1500s, when an unknown printer took a galley of type and scrambled it to
              make a type specimen book. It has survived not only five centuries.</p> -->
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
      title: `agroethical | ${this.service.name}`,
      meta: [
          {
            hid: 'description',
            name: 'description',
            content: this.service.summary
          },]
    }
  },

  asyncData(context) {
    return context.$api.fetchSingleServices(context.params.slug)
      .then(response => {
        return {
          service: response.services
        }
      })
      .catch(e => context.error(e))
  },
}
</script>
