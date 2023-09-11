<template>
  <div>
    <LazyPageHeader title="Shipping" />
    <section class="project_detail">
      <div class="container">
        <div class="row">
          <div class="col-xl-12 col-lg-12">
            <div class="project_detail_left_content">
              <div class="">
                <ul class="list-unstyled">
                  <li>
                    <div class="">
                      <div class="block-title">
                        <h3 class="">Trucks</h3>
                        <img v-lazy-load data-src="/assets/images/resources/leaf.png" alt="" />
                      </div>
                    </div>
                    <div class="row">
                      <div class="col-md-6 col-sm-12 mb-5">
                        <img v-lazy-load
                          class="rounded shadow"
                          data-src="/assets/images/shipping/shipping-image1.jpg"
                          style="width: 100%"
                        />
                      </div>
                      <div class="col-md-6 col-sm-12">
                        <p>
                          Transports via truck are conducted in accordance with
                          current international regulations. Our knowledgeable
                          staff and extensive experience ensure a quick and easy
                          processing. From the loading location to the final
                          destination, our skilled drivers assure the safe,
                          fast, and high-quality transportation of cattle.
                        </p>
                        <p>Equipment and care during transport:</p>

                        <ul class="">
                          <li>bedding in sawdust & straw</li>
                          <li>fully automized watering place</li>
                          <li>continuous feeding and care</li>
                          <li>climate controll and ventilation</li>
                          <li>skilled accompanying personal</li>
                        </ul>
                      </div>
                    </div>
                  </li>

                  <li class="mt-5">
                    <div class="">
                      <div class="block-title">
                        <h3 class="">Sea freight</h3>
                        <img v-lazy-load data-src="/assets/images/resources/leaf.png" alt="" />
                      </div>
                    </div>
                    <div class="row">
                      <div class="col-md-6 col-sm-12 order-1 order-md-0">
                        <p>
                          For big orders we can organize transport by vessel
                          according to valid regulations. The animals are
                          accompagnied till the place of loading on board under
                          supervision of a EU-vet. We employ a fleet of
                          specialized ships to regulate the quality of the
                          marine transportation of cattle. Through our team of
                          skilled stockmen and veterinarians sailing on the
                          vessels, strong business regulations, and high
                          technological requirements to the vessels, we provide
                          high animal welfare on board.
                        </p>
                        <p>Equipment and care during transport:</p>
                        <ul class="">
                          <li>bedding in sawdust & straw</li>
                          <li>sufficient water and fodder</li>
                          <li>EU-certification</li>
                          <li>Supervision by veterinarian during transport</li>
                        </ul>
                      </div>
                      <div class="col-md-6 col-sm-12 mb-5 order-0 order-md-1">
                        <img v-lazy-load
                          data-src="/assets/images/shipping/shipping-image2.jpg"
                          class="rounded shadow"
                          style="width: 100%"
                        />
                      </div>
                    </div>
                  </li>
                </ul>
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
      title: "Agroethical  | Shipping",
    };
  },
};
</script>
