<template>
  <v-card flat color="transparent">
    <v-card-title class="d-block custom-title text-center">
      Un duo père / fils
    </v-card-title>

    <div class="d-flex flex-row justify-center align-center flex-wrap">
      <v-card
        color="transparent"
        v-for="({ img, name, role }, i) in team"
        :key="i"
        class="ma-4 pa-4"
      >
        <v-img :src="img" position="contains" class="band-image" />
        <v-card-title
          class="black--text d-flex justify-center display-1 text-break pb-1"
        >
          {{ name }}
        </v-card-title>
        <v-card-text class="text-center pb-2 body-1 text-break">
          {{ role }}
        </v-card-text>
      </v-card>
    </div>
  </v-card>
</template>

<script>
export default {
  name: "Group",
  data() {
    return {
      team: [
        {
          img: require("@/assets/team/David.jpg"),
          name: "David Bouquet",
          role: "Papa & Chanteur"
        },
        {
          img: require("@/assets/team/Ewen.jpg"),
          name: "Ewen Bouquet",
          role: "Fiston & Guitariste"
        }
      ]
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

<style lang="scss">
@import "~vuetify/src/styles/styles.sass";

@media #{map-get(
    $display-breakpoints,
    "xs-only"
  )} {
  .band-image {
    max-width: inherit;
  }
}

@media #{map-get(
    $display-breakpoints,
    "sm-only"
  )} {
  .band-image {
    width: inherit;
  }
}

@media #{map-get(
    $display-breakpoints,
    "md-only"
  )} {
  .band-image {
    width: 400px;
  }
}

@media #{map-get(
    $display-breakpoints,
    "lg-only"
  )} {
  .band-image {
    width: 550px;
  }
}

@media #{map-get(
    $display-breakpoints,
    "xl-only"
  )} {
  .band-image {
    width: 750px;
  }
}
</style>
