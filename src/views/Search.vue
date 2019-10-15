<template>
  <div id="search">
      <searchcomponent v-on:SearchRequested="handleSearch"></searchcomponent>
      <previewplayer :player=player></previewplayer>
      <p v-if="isLoading">Loading</p>
  </div>
</template>

<script>

import Searchcomponent from '@/components/Searchcomponent.vue';
import Previewplayer from '@/components/Previewplayer.vue';


export default {
  name: 'search',
  components: { Searchcomponent, Previewplayer },
  data() {
    return {
      isLoading: false,
      player: [],
    };
  },
  methods: {
    doSearchQuery(url) {
      fetch(url)
        .then(res => res.json())
        .then((res) => {
          this.player = res;
          this.isLoading = false;
        });
    },
    handleSearch(username, platform) {
      this.player = [];
      const url = `https://api.bf4stats.com/api/playerInfo?plat=${platform}&name=${username}&output=json`;
      this.doSearchQuery(url);
      this.isLoading = true;
    },
  },
};
</script>
