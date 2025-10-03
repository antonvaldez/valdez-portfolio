<script setup>
  import { ref } from "vue";
  import { Notyf } from "notyf";
  import "notyf/notyf.min.css";

  const notyf = new Notyf();

// Web3Forms key (from your Web3Forms account)
  const WEB3FORMS_ACCESS_KEY = "96caf4ea-9932-4f87-ba02-62281ddfb7ea";
  const subject = "New message from Portfolio Contact Form";

  const name = ref("");
  const email = ref("");
  const message = ref("");

  const isLoading = ref(false);

  const submitForm = async () => {
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
          subject: subject,
          name: name.value,
          email: email.value,
          message: message.value,
        }),
      });

      const result = await response.json();

      if (result.success) {
        console.log(result);
        notyf.success("Message Sent!");
      // clear inputs
        name.value = "";
        email.value = "";
        message.value = "";
      } else {
        notyf.error("Something went wrong.");
      }
    } catch (error) {
      console.error(error);
      notyf.error("Failed to send message");
    } finally {
      isLoading.value = false;
    }
  };
</script>
