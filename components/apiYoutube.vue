<template>
  <div>
    <v-container>
      <v-row justify="center">
        <img src="../assets/img/pic.png" class="">
        <v-col cols="4">
          <v-text-field
            v-model="textSearch"
            label="Serach"
            :rules="rules"
            hide-details="auto"
            color="red darken-1"
          />
        </v-col>
        <v-col cols="1">
          <v-btn
            class="ma-2"
            tile
            color="red darken-1"
            dark
            @click="searchData()"
          >
            Search
          </v-btn>
        </v-col>
      </v-row>
    </v-container>
    <v-container>
      <v-row justify="center">
        <v-card
          v-for="list in playlist"
          :key="list.items"
          max-width="344"
          class="ml-6 mb-6"
        >
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title class="headline">
                {{ list.snippet.title }}
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-img :src="list.snippet.thumbnails.high.url" height="194" />
          <v-card-actions>
            <v-btn
              target="_blank"
              color="red darken-1"
              :href="'https://www.youtube.com/watch?v=' + list.id.videoId"
              class="mr-2"
            >
              PLAY VIDEO
            </v-btn>
            <nuxt-link
              :to="{ name: 'product-id', params: { id: list }}"
              style="text-decoration: none"
            >
              <v-btn color="red darken-1">
                Detail
              </v-btn>
              <v-spacer />
            </nuxt-link>
            <v-spacer />
            <v-btn icon color="blue lighten-2">
              <v-icon>mdi-thumb-up</v-icon>
            </v-btn>
            <v-btn icon color="red lighten-2">
              <v-icon>mdi-thumb-down</v-icon>
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      playlist: null,
      textSearch: ''
    }
  },

  methods: {
    searchData () {
      axios
        .get(
          'https://www.googleapis.com/youtube/v3/search?part=snippet&maxResults=50&q=' +
            this.textSearch +
            '&type=video&key=AIzaSyCYWUUmEvVkmbe3iiq_UZdR0-rRFMOc3_I'
        )

        .then((Response) => {
          this.playlist = Response.data.items // .slice(0, 20);
        })
        .catch((err) => {
          // eslint-disable-next-line no-console
          console.log(err)
          this.err = true
        })
    }
  }
}
</script>

<style>
body {
  background-color: #18191c;
}
</style>
