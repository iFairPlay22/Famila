<template>
  <v-container fluid>
    <v-layout row>
      <v-col
        offset-lg="3"
        lg="6"
        offset-sm="1"
        sm="10"
        offset="0"
        cols="12"
        class="pb-0"
      >
        <v-card flat color="transparent">
          <v-card-title
            class="mb-6 d-flex flex-row justify-center align-center"
          >
            <span class="text-uppercase text-break display-3 mr-2">
              {{ title }}
            </span>
            <v-btn icon @click="redirect(icon.link)">
              <v-icon class="black--text">{{ icon.icon }}</v-icon>
            </v-btn>
          </v-card-title>
          <v-card-text class="pb-0 text-justify text-break body-1">
            {{ description }}
          </v-card-text>
        </v-card>
      </v-col>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  name: "Description",
  data() {
    return {
      title: "Famila",
      description:
        "Vous vous mariez ? Vous organisez un événement familial ou privé ? Vous cherchez des musiciens pour votre bar, votre restaurant ? Famila, duo acoustique guitare-voix, vous propose d’animer vos réceptions et soirées avec des chansons françaises et internationales. Des années 60 à nos jours, Famila apportera l’accompagnement musical pour que vos invités ou clients passent un excellent moment.",
      icon: {
        icon: "mdi-facebook",
        link: "https://www.facebook.com/familamusique/"
      }
    };
  },
  methods: {
    redirect(link) {
      if (link !== "") {
        window.open(link, "_blank");
      }
    }
  }
};
</script>
