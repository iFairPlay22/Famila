<template>
  <div class="d-flex justify-space-around align-center">
    <v-card
      flat
      color="transparent"
      class="d-flex flex-column align-center justify-center my-3"
    >
      <v-card-title class="custom-title text-center mb-5 text-break"
        >Comment ça marche ?</v-card-title
      >
      <v-card
        flat
        color="transparent"
        class="d-flex flex-row justify-space-around align-start flex-wrap"
      >
        <v-card
          flat
          color="transparent"
          v-for="({ img, title, text }, i) in how"
          :key="i"
          class="d-flex flex-column justify-start align-center"
          max-width="20%"
          min-width="250px"
        >
          <v-img :src="img" max-width="200px" max-height="200px" />
          <v-card-title class="black--text text-center text-break">{{
            title
          }}</v-card-title>
          <v-card-text class="text-center body-1 text-break">{{
            text
          }}</v-card-text>
        </v-card>
      </v-card>
    </v-card>
  </div>
</template>

<script>
export default {
  name: "How",
  data() {
    return {
      how: [
        {
          img: require("@/assets/how/1.png"),
          title: "Contactez nous",
          text:
            "Remplissez le formulaire ci-dessous ou contactez nous sur les réseaux sociaux. Décrivez nous votre besoin."
        },
        {
          img: require("@/assets/how/3.png"),
          title: "Traitement de la demande",
          text:
            "Nous allons prendre en considération votre demande puis revenir vers vous."
        },
        {
          img: require("@/assets/how/4.png"),
          title: "Prestation",
          text:
            "C'est le jour J, il est temps de vous faire chanter et danser ! :)"
        }
      ]
    };
  }
};
</script>
