<template>

  <div class="search">
    <img alt="BF4 logo" src="../assets/bf4.png" class="center">
    <input type="text" v-model="username" placeholder="User account name" @keypress.enter="handleSearch"/>
    <select v-model="platform">
      <option value="" disabled>Select a platform</option>
      <option v-for="option in options" v-bind:value="option.value">
        {{ option.text }}
      </option>
    </select>
    <button @click="handleSearch">Search</button>
  </div>
</template>

<script>
/* eslint-disable */
export default {
  data() {
    return {
      username: '',
      platform: '',
      options: [
      { text: 'Playstation 4', value: 'ps4' },
      { text: 'Playstation 3', value: 'ps3' },
      { text: 'PC', value: 'pc' },
      { text: 'XBOX 360', value: 'xbox' },
      { text: 'XBOX ONE', value: 'xone' },
      ]
    }
  },
  methods: {
    handleSearch() {
      this.$emit('SearchRequested', this.username, this.platform);
    }
  }
};
</script>


