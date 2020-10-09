<template>
  <div>
    <v-card
      flat
      color="transparent"
      class="d-flex align-center justify-center my-3"
    >
      <v-card-title class="custom-title text-center">Le groupe</v-card-title>
    </v-card>

    <div class="d-flex flex-row justify-center flex-wrap">
      <v-card
        color="transparent"
        v-for="({ img, name, role }, i) in team"
        :key="i"
        :width="imageDimentions"
        min-width="300px"
        class="ma-10"
      >
        <v-img
          :src="img"
          :width="imageDimentions"
          :height="imageDimentions"
          min-width="300px"
          min-height="300px"
          position="contains"
        />
        <v-card-title
          class="black--text d-flex justify-center display-1 text-break"
          >{{ name }}</v-card-title
        >
        <v-card-text class="text-center pb-2 title text-break">{{
          role
        }}</v-card-text>
      </v-card>
    </div>
  </div>
</template>

<script>
export default {
  name: "Group",
  mounted() {
    this.$nextTick(() => {
      window.addEventListener("resize", this.onResize);
    });
  },
  beforeDestroy() {
    window.removeEventListener("resize", this.onResize);
  },
  computed: {
    imageDimentions() {
      return this.windowWidth / (this.team.length + 1);
    }
  },
  data() {
    return {
      windowWidth: window.innerWidth,
      team: [
        {
          img: require("@/assets/team/David.jpg"),
          name: "David Bouquet",
          role: "Chanteur"
        },
        {
          img: require("@/assets/team/Ewen.jpg"),
          name: "Ewen Bouquet",
          role: "Guitariste"
        }
      ]
    };
  },
  methods: {
    onResize() {
      this.windowWidth = window.innerWidth;
    },
    redirect(link) {
      if (link !== "") {
        window.open(link, "_blank");
      }
    }
  }
};
</script>
