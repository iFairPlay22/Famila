<template>
  <v-card flat color="transparent">
    <v-card-title class="d-block custom-title text-center">
      Comment ça marche ?
    </v-card-title>

    <div class="d-flex flex-row justify-center align-center flex-wrap">
      <v-card
        v-for="({ img, title, text }, i) in how"
        :key="i"
        flat
        color="transparent"
        class="d-flex flex-column align-center"
      >
        <v-img :src="img" max-width="150px" max-height="150px" />
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
    </div>
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
