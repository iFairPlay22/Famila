<template>
  <v-bottom-navigation
    app
    background-color="white"
    color="black"
    dark
    horizontal
    scroll-threshold="0"
    hide-on-scroll
  >
    <v-btn
      v-for="({ title, icon, link }, i) in icons"
      :key="i"
      @click="redirect(link)"
    >
      <span class="subtitle-1 black--text">{{ title }}</span>
      <!-- black -->
      <v-icon class="black--text">{{ icon }}</v-icon>
      <!-- black -->
    </v-btn>
  </v-bottom-navigation>
</template>

<script>
export default {
  name: "MastFoot",
  data() {
    return {
      icons: [
        {
          title: "Facebook",
          icon: "mdi-facebook",
          link: "https://www.facebook.com/familamusique/",
        },
        {
          title: "Youtube",
          icon: "mdi-youtube",
          link: "https://www.youtube.com/channel/UCMswW4S2kno9IwZO-qXualw",
        },
      ],
    };
  },
  methods: {
    redirect(link) {
      if (link !== "") {
        window.open(link, "_blank");
      }
    },
  },
};
</script>
