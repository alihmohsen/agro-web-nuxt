<template>
  <div>
    <LazyPageHeader title="About" />
    <section class="about_two">
      <div class="container">
        <div class="row">
          <div class="col-xl-12 col-lg-12 col-md-12 mb-5">
            <b>
              We are your expert business partner, bringing live animals from
              Europe and South America to markets around the globe.
            </b>

            <p>
              We are a seasoned and forward-thinking business offering services
              globally. By improving animal husbandry and raising the bar for
              quality, our specialized and experienced team has advanced to the
              top for our nation.
            </p>
            <p>
              We are taking great care to ensure that the animals that will
              enter our country are of the highest quality by behaving in
              accordance with our national sentiments. In our capacity as a
              distribution company, we primarily import and export breeding
              pregnant heifers, milk cows, fattening cattle, and animals of all
              racial groups. Consultancy work for cattle firms is one of our
              business's most significant endeavors. We are experts in the
              mediation of premium breeding animals!Our goal is to offer the
              finest price-performance ratio possible by leveraging our
              company's experience, power, and solid connections. We would like
              to provide you the chance to view and select our livestock for
              breeding and fattening.
            </p>
          </div>
          <div class="col-xl-3 col-lg-3 col-md-3">
            <div class="block-title text-left">
              <h3>Mission</h3>
              <div class="leaf">
                <img v-lazy-load data-src="/assets/images/resources/leaf.png" alt="" />
              </div>
            </div>
          </div>
          <div class="col-xl-9 col-lg-9 col-md-9">
            <div class="about_two_text">
              <p>
                Our mission is to handle specialized export requirements and
                deliver high quality cattle and livestock products. We do this
                by offering catered, hassle-free and end to end services and
                solutions to our esteemed clients in the middle east and North
                Africa region.
              </p>
            </div>
          </div>
        </div>

        <div class="row mt-5">
          <div class="col-xl-3 col-lg-3 col-md-3">
            <div class="block-title text-left">
              <h3>Vision</h3>
              <div class="leaf">
                <img v-lazy-load data-src="/assets/images/resources/leaf.png" alt="" />
              </div>
            </div>
          </div>
          <div class="col-xl-9 col-lg-9 col-md-9">
            <div class="about_two_text">
              <p>
                A one-stop reliable partner for all of our clients’ needs in
                cattle and livestock business .
              </p>
            </div>
          </div>
        </div>

        <div class="row mt-5">
          <div class="col-xl-3 col-lg-3 col-md-3">
            <div class="block-title text-left">
              <h3>Values</h3>
              <div class="leaf">
                <img v-lazy-load data-src="/assets/images/resources/leaf.png" alt="" />
              </div>
            </div>
          </div>
          <div class="col-xl-9 col-lg-9 col-md-9">
            <div class="about_two_text">
              <p>
                our values is professionalism, integrity, long-term commitment,
                adaptability, passion, ensuring customer satisfaction.
              </p>
            </div>
          </div>
        </div>
      </div>
    </section>
    <!-- <LazyBrandOne />
    <LazyVideoOne />
    <LazyProductOne />
    <LazyTeamOne />
    <LazyCallToActionOne /> -->
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: "Agroethical  | About",
    };
  },
};
</script>
