<template>
  <div class="container" id="contact">
    <h2>Contact me!</h2>
    <div class="row my-5 justify-content-center">
      <div class="col-md-6">
        <form @submit.prevent="submitForm">
          <input
            type="text"
            v-model="name"
            placeholder="First Name, Last Name"
            class="form-control"
            required
            autocomplete="name"
          />
          <input
            type="email"
            v-model="email"
            placeholder="Email"
            class="form-control mt-1"
            required
            autocomplete="email"
          />
          <textarea
            rows="5"
            v-model="message"
            class="form-control mt-1"
            placeholder="Enter your message here..."
            required
          ></textarea>

          <!-- reCAPTCHA container -->
          <div ref="recaptchaContainer" class="my-3"></div>

          <div class="d-flex justify-content-center gap-2 mt-3">
            <a href="https://www.linkedin.com/in/antonvaldez/" target="_blank">
              <img src="https://cdn-icons-png.flaticon.com/256/174/174857.png" />
            </a>
            <a href="https://github.com/antonvaldez" target="_blank">
              <img src="https://cdn-icons-png.flaticon.com/256/25/25231.png" />
            </a>
            <button type="submit" class="form-button ms-auto" :disabled="isLoading">
              {{ isLoading ? "Sending..." : "Submit" }}
            </button>
            <button type="reset" class="form-button" @click="resetForm">Reset</button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";
import { Notyf } from "notyf";
import "notyf/notyf.min.css";

const notyf = new Notyf();

// Web3Forms config
const WEB3FORMS_ACCESS_KEY = "96caf4ea-9932-4f87-ba02-62281ddfb7ea";
const subject = "New message from Portfolio Contact Form";

const name = ref("");
const email = ref("");
const message = ref("");
const isLoading = ref(false);

// reCAPTCHA refs
const recaptchaContainer = ref(null);
const recaptchaWidgetId = ref(null);
const recaptchaToken = ref("");

// Your reCAPTCHA site key
const SITE_KEY = "6LeH7NwrAAAAAJNrL9W7DGMjCSM531FtvmE6jY9M";

function loadRecaptchaScript(callback) {
  if (document.getElementById("recaptcha-script")) {
    callback();
    return;
  }

  const script = document.createElement("script");
  script.id = "recaptcha-script";
  script.src = "https://www.google.com/recaptcha/api.js?render=explicit";
  script.async = true;
  script.defer = true;
  script.onload = callback;
  document.head.appendChild(script);
}

// reCAPTCHA callbacks
function onRecaptchaSuccess(token) {
  recaptchaToken.value = token;
}
function onRecaptchaExpired() {
  recaptchaToken.value = "";
}

// Render reCAPTCHA
function renderRecaptcha() {
  if (!window.grecaptcha) {
    console.error("reCAPTCHA not loaded");
    return;
  }
  recaptchaWidgetId.value = window.grecaptcha.render(recaptchaContainer.value, {
    sitekey: SITE_KEY,
    size: "normal",
    callback: onRecaptchaSuccess,
    "expired-callback": onRecaptchaExpired,
  });
}

// Reset reCAPTCHA
function resetRecaptcha() {
  if (recaptchaWidgetId.value !== null) {
    window.grecaptcha.reset(recaptchaWidgetId.value);
    recaptchaToken.value = "";
  }
}

// Reset form function
const resetForm = () => {
  name.value = "";
  email.value = "";
  message.value = "";
  resetRecaptcha();
};

// Submit form function
const submitForm = async () => {
  if (!recaptchaToken.value) {
    notyf.error("Please verify that you are not a robot.");
    return;
  }

  isLoading.value = true;
  try {
    const response = await fetch("https://api.web3forms.com/submit", {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
        Accept: "application/json",
      },
      body: JSON.stringify({
        access_key: WEB3FORMS_ACCESS_KEY,
        subject,
        name: name.value,
        email: email.value,
        message: message.value,
      }),
    });

    const result = await response.json();

    if (result.success) {
      notyf.success("Message Sent!");
      resetForm();
    } else {
      notyf.error("Something went wrong.");
    }
  } catch (error) {
    console.error(error);
    notyf.error("Failed to send message");
  } finally {
    isLoading.value = false;
    resetRecaptcha();
  }
};

// Render reCAPTCHA on mount
onMounted(() => {
  const interval = setInterval(() => {
    if (window.grecaptcha && window.grecaptcha.render) {
      renderRecaptcha();
      clearInterval(interval);
    }
  }, 100);

  onBeforeUnmount(() => {
    clearInterval(interval);
  });
});
</script>
