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
      <v-icon class="black--text">{{ icon }}</v-icon>
    </v-btn>
  </v-bottom-navigation>
</template>

<script>
export default {
  name: "MastFoot",
  props: ["icons"],
  methods: {
    redirect(link) {
      if (link !== "") {
        window.open(link, "_blank");
      }
    }
  }
};
</script>
