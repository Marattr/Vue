<template>
  <div>
    <center>
      <img alt="BF4 logo" src="../assets/bf4.png">
      <h2>Battlefiled 4 All Platforms Online Player Count</h2>
      <ul>
        <li v-bind:key="bf4stats" v-for="players in bf4stats">
          <strong>{{players.label}} :</strong>
          {{players.count}} Peak Number in Last 24 Hour: {{players.peak24}}
        </li>
      </ul>
    </center>
  </div>
</template>

<script>
export default {
  props: ['bf4stats'],
};
</script>
