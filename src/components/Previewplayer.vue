<template>
  <div>
    <br>
    <span v-bind:key="player" v-for="(val, key) in player">
      <span v-if="key === 'error'">
        <strong>ERROR!</strong> Please enter user account name and/or select platform again.
      </span>
    </span>
    <span v-bind:key="player" v-for="(val, key, index) in player">
      <span v-if="key !== 'error' && index === 0">
        <strong>PLAYER STATS</strong>
      </span>
    </span>
    <ul>
      <li v-bind:key="player" v-for="(value, name, index) in player">
        <span v-if= "index==0 && value.uName != null">
          <strong>Username: </strong> {{value.uName}}
        </span>
        <span v-if= "index==0 && value.uName != null">
          <strong> Total Score: </strong> {{value.score}}
        </span>
        <span v-if= "index==0 && value.lastDay != null">
          <strong> Last Day Online: </strong> {{value.lastDay}}
        </span>
        <span v-if= "index==0 && value.timePlayed != null">
          <strong> Time played: </strong> {{ timePlayed(value) }} Hours
        </span>
        <span v-if= "index==1">
          <strong>Rank: </strong> {{value.rank}}
        </span>
        <span v-if= "index==1">
          <strong> Total Kills: </strong> {{value.kills}}
        </span>
        <span v-if= "index==1">
          <strong> Total Deaths: </strong> {{value.deaths}}
        </span>
        <span v-if= "index==1">
          <strong> Headshots: </strong> {{value.headshots}}
        </span>
        <span v-if= "index==1">
          <strong> Round Wins: </strong> {{value.numWins}}
        </span>
        <span v-if= "index==1">
          <strong> Round Losses: </strong> {{value.numLosses}}
        </span>
        <br>
        <span v-if= "index==1">
          <span v-bind:key="value" v-for="(val, key, index) in value.extra">
            <span v-if= "index==0">
              <strong> Kill / Death: </strong> {{editNumber(val)}}
            </span>
          </span>
        </span>
        <span v-if= "index==1">
          <span v-bind:key="value" v-for="(val, key, index) in value.extra">
            <span v-if= "index==2">
              <strong> Score Per Minute: </strong> {{editNumber(val)}}
            </span>
          </span>
        </span>
        <span v-if= "index==1">
          <span v-bind:key="value" v-for="(val, key, index) in value.extra">
            <span v-if= "index==8">
              <strong> Accuracy: </strong> {{editNumber(val)}}
            </span>
          </span>
        </span>
        <span v-if= "index==1">
          <span v-bind:key="value" v-for="(val, key, index) in value.extra">
            <span v-if= "index==25">
              <strong> Medals: </strong> {{val}}
            </span>
          </span>
        </span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['player'],
  computed: {
    error() {
      return Object.keys(this.player) === 'error';
    },
  },
  methods: {
    timePlayed(value) {
      let time = 0;
      time = value.timePlayed / 3600;
      return time.toFixed(2);
    },
    editNumber(value) {
      let num = 0;
      num = value;
      return num.toFixed(4);
    },
  },
};
</script>
