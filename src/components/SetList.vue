<template>
  <v-container fluid>
    <!-- Title -->
    <v-layout row>
      <v-col offset="0" cols="12">
        <v-card flat color="transparent">
          <v-card-title class="d-block custom-title text-center">
            Nos reprises
          </v-card-title>
        </v-card>
      </v-col>
    </v-layout>

    <!-- Search -->
    <v-layout row>
      <v-col offset-md="3" md="6" offset-sm="2" sm="8" offset="0" cols="12">
        <v-text-field
          v-model="search"
          placeholder="Rechercher"
          append-icon="mdi-magnify"
          class="custum-text-input"
          outlined
          @keydown.enter="fetchSongs"
        />
      </v-col>
    </v-layout>

    <!-- Results -->
    <div v-for="(showedSong, id) in showedSongs" :key="id">
      <v-layout row>
        <v-col offset-md="3" md="6" offset-sm="2" sm="8" offset="0" cols="12">
          <!-- Song -->
          <div :key="id">
            <v-divider></v-divider>
            <v-list-item class="grow">
              <v-list-item-avatar
                class="d-none d-sm-block ma-0"
                color="transparent"
              >
                <v-icon icon color="black">mdi-music-note-eighth</v-icon>
              </v-list-item-avatar>

              <v-list-item-title class="d-flex d-lg-block flex-column my-2">
                <span class="title text-wrap">
                  {{ showedSong.songName }}
                </span>
                <span class="subtitle text-wrap">
                  {{ showedSong.groupName }}
                </span>
              </v-list-item-title>
            </v-list-item>
            <v-divider></v-divider>
          </div>
        </v-col>
      </v-layout>
    </div>

    <!-- Pagination -->
    <v-layout row justify="end">
      <v-col cols="12">
        <v-pagination
          class="mb-10"
          v-model="pagination.currentPage"
          :total-visible="pagination.resultsByPage"
          :length="nbPages"
          @input="updateShowedSongs"
        >
        </v-pagination>
      </v-col>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  name: "SetList",
  mounted() {
    this.fetchSongs();
  },
  data() {
    return {
      pagination: {
        currentPage: 1,
        resultsByPage: 5
      },
      search: "",
      songs: [],
      showedSongs: []
    };
  },
  methods: {
    fetchSongs() {
      this.songs = [];
      this.pagination.currentPage = 1;

      fetch(
        `https://my-bands-app.herokuapp.com/index.php/api/songs/Maitris%C3%A9e/${this.search}`
      )
        .then(response => response.json())
        .then(json => (this.songs = json))
        .then(() => this.updateShowedSongs())
        .catch(e => console.error(e));
    },
    updateShowedSongs() {
      if (this.songs.length == 0) {
        this.showedSongs = [];
        return;
      }

      const startIndex =
        (this.pagination.currentPage - 1) * this.pagination.resultsByPage;
      const lastIndex = startIndex + this.pagination.resultsByPage;

      this.showedSongs = this.songs.slice(startIndex, lastIndex);
    }
  },
  computed: {
    nbPages() {
      return Math.floor(this.songs.length / this.pagination.resultsByPage) + 1;
    }
  }
};
</script>

<style></style>
