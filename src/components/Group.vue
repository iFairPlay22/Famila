<template>
  <v-card flat color="transparent">
    <v-card-title class="d-block custom-title text-center">
      Le groupe
    </v-card-title>

    <v-container fluid>
      <v-layout row>
        <v-col
          :offset-sm="i != 0 ? 0 : 1"
          sm="5"
          offset="0"
          cols="12"
          v-for="({ img, name, role }, i) in team"
          :key="i"
        >
          <v-card color="transparent">
            <v-img :src="img" position="contains" />
            <v-card-title
              class="black--text d-flex justify-center display-1 text-break pb-1"
            >
              {{ name }}
            </v-card-title>
            <v-card-text class="text-center pb-2 body-1 text-break">
              {{ role }}
            </v-card-text>
          </v-card>
        </v-col>
      </v-layout>
    </v-container>
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
