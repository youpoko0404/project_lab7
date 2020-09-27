<template>
  <div>
    <v-card
      :loading="loading"
      class="mx-auto my-12"
      max-width="1600"
    >
      <v-row align="center" justify="center">
        <iframe
          width="1600"
          height="670"
          :src="'https://www.youtube.com/embed/' + this.$route.params.id.id.videoId "
          frameborder="0"
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen
          aspect-ratio="1"
          class="grey lighten-2"
        />
      </v-row>
      <v-card-title><h2>{{ this.$route.params.id.snippet.title }}</h2></v-card-title>
      <v-card-text>
        <div class="subtitle-1">
          <h3>
            <font color="grey">
              Description : {{ this.$route.params.id.snippet.description }}
            </font>
          </h3>
        </div>
        <div class="subtitle-1">
          <h3>
            <a
              style="text-decoration: none;"
              target="_blank"
              :href="'https://www.youtube.com/channel/' + this.$route.params.id.snippet.channelId "
            ><font color="grey">Channel : {{ this.$route.params.id.snippet.channelTitle }}</font></a>
          </h3>
        </div>
      </v-card-text>
      <hr>
    </v-card>
  </div>
</template>
