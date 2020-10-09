<template>
  <v-card flat color="transparent" class="my-8">
    <v-card-title class="custom-title text-center mb-5 text-break"
      >Formulaire de contact</v-card-title
    >
    <v-form
      ref="form"
      v-model="isValid"
      class="d-flex flex-column justify-space-around"
    >
      <v-text-field
        v-model="form.data.name"
        :rules="form.rules.name"
        placeholder="Votre nom"
        required
      ></v-text-field>
      <v-text-field
        v-model="form.data.email"
        :rules="form.rules.email"
        placeholder="Votre email"
        required
      ></v-text-field>
      <v-text-field
        v-model="form.data.phone"
        :rules="form.rules.phone"
        placeholder="Votre numéro de téléphone"
      ></v-text-field>
      <v-textarea
        v-model="form.data.message"
        :rules="form.rules.message"
        placeholder="Votre demande"
        required
      ></v-textarea
      ><v-btn tile color="success" @click="sendForm" :disabled="!isValid">
        <v-icon left>
          mdi-pencil
        </v-icon>
        Edit
      </v-btn></v-form
    >
    <v-snackbar v-model="snackbar.active" :timeout="snackbar.timeout">
      {{ snackbar.text() }}

      <template v-slot:action="{ attrs }">
        <v-btn
          :color="snackbar.color()"
          text
          v-bind="attrs"
          @click="snackbar.active = false"
        >
          Close
        </v-btn>
      </template>
    </v-snackbar>
  </v-card>
</template>

<script>
export default {
  name: "ContactForm",
  data() {
    return {
      isValid: false,
      snackbar: {
        active: false,
        timeout: 5000,
        ok: true,
        text: () =>
          this.snackbar.ok
            ? "Votre demande a bien été prise en compte."
            : "Votre demande n'a pas été prise en compte",
        color: () => (this.snackbar.ok ? "green" : "red")
      },
      form: {
        data: {
          name: "",
          email: "",
          phone: "",
          message: ""
        },
        rules: {
          name: [v => !!v || "Name is required"],
          email: [
            v => !!v || "E-mail is required",
            v => /.+@.+\..+/.test(v) || "E-mail must be valid"
          ],
          phone: [
            v => !!v || "Phone is required",
            v =>
              /(^0[0-9]{9}$)|(^0[0-9]( [0-9]{2}){4}$)/.test(v) ||
              "Phone must be a valid phone"
          ],
          message: [
            v => !!v || "Message is required",
            v =>
              (v && 20 <= v.length) ||
              "Message must be less than 20 characters",
            v =>
              (v && v.length <= 500) ||
              "Message must be less than 500 characters"
          ]
        }
      }
    };
  },
  methods: {
    sendForm() {
      if (!this.isValid) return;

      fetch("https://api.emailjs.com/api/v1.0/email/send", {
        mode: "cors",
        method: "POST",
        headers: {
          "Content-type": "application/json"
        },
        body: JSON.stringify({
          service_id: "service_b3qh7ej",
          template_id: "template_zbxe3j4",
          user_id: "user_wl0Ew9bwIay0RJlT6sIbx",
          template_params: {
            owner_name: "David Bouquet",
            owner_email: "davidbouquet.musique@gmail.com",
            client_name: this.form.data.name,
            client_email: this.form.data.email,
            client_phone: this.form.data.phone,
            client_message: this.form.data.message
          }
        })
      })
        .then(response => {
          this.snackbar.ok = response.ok;
          if (response.ok) {
            this.form.data = {
              name: "",
              email: "",
              phone: "",
              message: ""
            };
            this.$refs["form"].reset();
          }
        })
        // .catch((error) => {
        //   this.snackbar.ok = false;
        //   console.log(error);
        // })
        .finally(() => {
          this.snackbar.active = true;
        });
    }
  }
};
</script>
