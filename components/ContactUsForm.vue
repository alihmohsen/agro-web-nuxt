<template>

      <form class="row" @submit.prevent="send">
        <div class="col-md-6">
          <div class="input_box mb-3">
            <div class="input-group">
              <input
                :class="errors.name ? 'error' : ''"
                type="text"
                v-model="form.name"
                name="name"
                placeholder="Full name"
                required
              />
              <span v-if="errors.name">this field is required</span>
            </div>
          </div>
        </div>
        <div class="col-md-6">
          <div class="input_box mb-3">
            <div class="input-group">
              <input
                :class="errors.email ? 'error' : ''"
                type="email"
                name="email"
                v-model="form.email"
                placeholder="Email Address"

              />
              <span v-if="errors.email">this field is required</span>
            </div>
          </div>
        </div>
        <div class="col-md-6">
          <div class="input_box mb-3">
            <div class="input-group">
              <input
                :class="errors.phone ? 'error' : ''"
                type="text"
                name="phone"
                v-model="form.phone"
                placeholder="Phone"
                required
              />
              <span v-if="errors.phone">this field is required</span>
            </div>
          </div>
        </div>
        <div class="col-md-6">
          <div class="input_box mb-3">
            <div class="input-group">
              <input
                :class="errors.subject ? 'error' : ''"
                type="text"
                name="subject"
                placeholder="Subject"
                v-model="form.subject"

              />
              <span v-if="errors.subject">this field is required</span>
            </div>
          </div>
        </div>
        <div class="col-md-12">
          <div class="input_box mb-3">
            <div class="input-group">
              <textarea
                :class="errors.message ? 'error' : ''"
                type="text"
                name="message"
                placeholder="Write Message"
                v-model="form.message"

              ></textarea>
              <span v-if="errors.message">this field is required</span>
            </div>
          </div>
        </div>
        <div class="col-md-12 my-1">
          <div class="input_box">
            <button type="submit" class="thm-btn contact-one__btn">Send a Request</button>
          </div>
        </div>
      </form>

</template>
<script>
export default {
  data() {
    return {
      form: {
        name: "",
        email: "",
        phone: "",
        subject: "",
        message: "",
      },
      Validate: true,
      errors: {
        name: false,
        phone: false,
      },
    };
  },
  methods: {
   async send() {
      for (let f in this.errors) {
        if (this.form[f] == "" || this.form[f] == null) {
          this.errors[f] = true;
          this.Validate = false;
        } else {
          this.errors[f] = false;
        }
      }
      if (this.Validate) {
       const  responce = await this.$api.fetchContactUs(this.form);
        this.$toast.success("successfull submitted");
        for (let f in this.form) {
            this.form[f] = '';
        }
      }
    },
  },
};
</script>
