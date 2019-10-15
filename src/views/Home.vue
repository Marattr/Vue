<template>
  <div class="home">
    <preview :bf4stats=bf4stats></preview>
    <p v-if="isLoading">Loading</p>
  </div>
</template>

<script>
// @ is an alias to /src
import Preview from '@/components/Preview.vue';

export default {
  name: 'home',
  components: { Preview },
  data() {
    return {
      isLoading: true,
      bf4stats: [],
    };
  },
  methods: {
    doQuery(url) {
      fetch(url)
        .then(res => res.json())
        .then((res) => {
          this.bf4stats = res;
          this.isLoading = false;
        });
    },
  },
  created() {
    const url = 'https://api.bf4stats.com/api/onlinePlayers';
    this.doQuery(url);
  },
};
</script>
