<template>
  <v-container fluid>
    <v-layout row>
      <v-col offset-lg="1" lg="10" offset-md="1" md="10" offset-sm="0" sm="12">
        <v-card
          flat
          color="transparent"
          class="d-flex flex-column align-center justify-space-around"
        >
          <v-card-title class="custom-title text-center mb-7 text-break"
            >Prestations</v-card-title
          >
          <div
            style="position: relative; width: 100%; height: 0; padding-bottom: 56.25%;"
          >
            <iframe
              frameborder="0"
              allowfullscreen
              style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"
              src="https://www.youtube.com/embed/JPzpCr8i_qU"
            ></iframe>
          </div>
        </v-card>
      </v-col>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  name: "Video"
};
</script>
