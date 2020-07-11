<template>
  <v-container>
    <v-flex xs12 pb-16>
      <h1 class="text-center">Latest News</h1>
    </v-flex>

    <v-flex xs12 pb-10 offset-sm2 v-for="(item, i) in articles" :key="i">
      <v-card max-width="80%">
        <img width="100%" height="200px" :src="item.urlToImage" />
        <v-card-title class="justify-center">{{ item.title }}</v-card-title>
        <v-spacer />
        <v-card-subtitle class="pb-0">{{ item.author }}</v-card-subtitle>

        <v-card-text class="text--primary">
          <div>{{ item.content }}</div>
        </v-card-text>

        <v-card-actions class="justify-center">
          <v-btn flat :href="item.url" target="_blank"> More</v-btn>
        </v-card-actions>
      </v-card>
    </v-flex>
  </v-container>
</template>

<script>
export default {
  async asyncData(app) {
    const { articles } = await app.$axios.$get(process.env.keyurl);
    return { articles };
  }
};
</script>
