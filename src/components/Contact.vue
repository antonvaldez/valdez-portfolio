<template>
  <div class="container" id="contact">
    <h2>Contact me!</h2>
    <div class="row my-5 justify-content-center">
      <div class="col-md-6">
        <form @submit.prevent="submitForm">
          <input
            type="text"
            name="name"
            v-model="form.name"
            placeholder="First Name, Last Name"
            class="form-control"
            required
            autocomplete
          />
          <input
            type="email"
            name="email"
            v-model="form.email"
            placeholder="Email"
            class="form-control mt-1"
            required
            autocomplete
          />
          <textarea
            rows="5"
            class="form-control mt-1"
            placeholder="Enter your message here..."
            v-model="form.message"
            required
          ></textarea>

          <div class="d-flex justify-content-center gap-2 mt-3">
            <a href="https://www.linkedin.com/" target="_blank">
              <img src="https://cdn-icons-png.flaticon.com/256/174/174857.png" />
            </a>
            <a href="https://github.com" target="_blank">
              <img src="https://cdn-icons-png.flaticon.com/256/25/25231.png" />
            </a>
            <a href="https://about.gitlab.com" target="_blank">
              <img
                src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQTMU0Ge8750e3MFRuLtBi_nu8MlsLnuCT5UQ&s"
              />
            </a>
            <button type="submit" class="form-button ms-auto">Submit</button>
            <button type="reset" class="form-button">Reset</button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import { Notyf } from "notyf";
import "notyf/notyf.min.css";

export default {
  name: "Contact",
  data() {
    return {
      form: {
        name: "",
        email: "",
        message: "",
      },
      notyf: new Notyf(),
    };
  },
  methods: {
    async submitForm() {
      try {
        const response = await fetch("https://api.web3forms.com/submit", {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
            Accept: "application/json",
          },
          body: JSON.stringify({
            access_key: "96caf4ea-9932-4f87-ba02-62281ddfb7ea",
            ...this.form,
          }),
        });

        const result = await response.json();

        if (result.success) {
          this.notyf.success("Message sent successfully!");
          this.form.name = "";
          this.form.email = "";
          this.form.message = "";
        } else {
          this.notyf.error("Something went wrong. Please try again.");
        }
      } catch (error) {
        this.notyf.error("Error sending message. Please try again.");
      }
    },
  },
};
</script>