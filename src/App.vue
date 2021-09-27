<template>
  <v-app>
    <mast-head :icons="icons" />

    <v-content>
      <router-view />
    </v-content>

    <mast-foot :icons="icons" />
  </v-app>
</template>

<script>
import MastHead from "./components/MastHead";
import MastFoot from "./components/MastFoot";

export default {
  name: "App",
  components: {
    MastHead,
    MastFoot
  },
  data() {
    return {
      icons: [
        {
          title: "Facebook",
          icon: "mdi-facebook",
          link: "https://www.facebook.com/familamusique/"
        },
        {
          title: "Youtube",
          icon: "mdi-youtube",
          link: "https://www.youtube.com/channel/UCMswW4S2kno9IwZO-qXualw"
        }
      ]
    };
  }
};
</script>

<style lang="scss">
@import "~vuetify/src/styles/styles.sass";

.custom-title {
  font-size: 2.5rem !important;
}

.custom-bar-title {
  font-size: 2.5rem !important;
}

@media #{map-get(
    $display-breakpoints,
    "xs-only"
  )} {
  .custom-title {
    font-size: 2rem !important;
  }

  .custom-bar-title {
    font-size: 1.2rem !important;
  }
}
</style>
