<template>
  <v-card flat color="transparent">
    <v-card-title class="d-block custom-title text-center">
      Comment ça marche ?
    </v-card-title>

    <v-container fluid>
      <v-layout row>
        <v-col
          v-for="({ img, title, text }, i) in how"
          :key="i"
          offset-sm="0"
          sm="4"
          offset="0"
          cols="12"
        >
          <v-card
            flat
            color="transparent"
            class="d-flex flex-column align-center"
          >
            <v-img :src="img" max-width="175px" max-height="175px" />
            <v-card-title class="pt-0 black--text text-center text-break">
              {{ title }}
            </v-card-title>
            <v-card-text
              class="text-center body-1 text-break"
              style="max-width:400px"
            >
              {{ text }}
            </v-card-text>
          </v-card>
        </v-col>
      </v-layout>
    </v-container>
  </v-card>
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
