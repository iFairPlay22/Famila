<template>
  <v-app-bar
    app
    color="white"
    light
    dense
    prominent
    scroll-threshold="0"
    hide-on-scroll
  >
    <v-card
      flat
      color="transparent"
      height="100%"
      class="d-flex justify-center align-center"
    >
      <v-img
        height="80px"
        width="80px"
        position="contains"
        src="@/assets/logo.png"
      ></v-img>
      <v-card-title
        class="d-none d-sm-block ml-3 black--text custom-bar-title text-break"
      >
        Groupe Famila
      </v-card-title>
    </v-card>
    <div class="flex-grow-1"></div>
    <v-btn
      icon
      v-for="({ icon, link }, i) in icons"
      :key="i"
      @click="redirect(link)"
    >
      <v-icon class="black--text">{{ icon }}</v-icon>
    </v-btn>
  </v-app-bar>
</template>

<script>
export default {
  name: "MastHead",
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
