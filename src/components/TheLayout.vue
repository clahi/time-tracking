<template>
  <div class="container">
    <div class="personContainer rounded">
      <div class="person rounded-3">
        <img src="../assets/image-jeremy.png" class="img-fluid" alt="" />
        <div class="about">
          <p class="text-muted">Report for</p>
          <h3 class="my-0">Jeremy &nbsp;</h3>
          <h3 class="my-1">Robson</h3>
        </div>
      </div>
      <div class="time rounded-bottom">
        <button @click="when('daily')">Daily</button>
        <button @click="when('weekly')">Weekly</button>
        <button @click="when('monthly')">Monthly</button>
      </div>
    </div>
    <track-items
      class="track"
      v-for="track in trackItems"
      :key="track"
      :trackItem="track"
      :timeFrame="track.timeframes[time]"
      :time="time"
    ></track-items>
  </div>
</template>

<script>
import TrackItems from "./TrackItems.vue";
export default {
  components: {
    TrackItems,
  },
  data() {
    return {
      trackItems: [],
      time: "weekly"
    };
  },
  methods: {
    when(val) {
      this.time = val
    }
  },
  created() {
    const TrackItems = this.$store.getters["trackItems"]
    this.trackItems = TrackItems
    console.log(this.trackItems)
    console.log(TrackItems)
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  color: white;
}

.personContainer {
  background-color: hsl(235, 46%, 20%);
}

h3 {
  display: inline-block;
}

.person {
  background-color: hsl(235, 45%, 61%);
  display: flex;
  padding: 1em;
  align-items: center;
}

.time {
  display: flex;
  justify-content: space-around;
  align-items: center;
  padding-bottom: 1.5em;
}

.time > button {
  background-color: transparent;
  border: none;
  color: hsl(236, 100%, 87%);
}

.time > button:hover {
  color: white;
}

.time > button + button {
  margin-top: 0;
}

img {
  align-self: center;
  /* padding-left: 1em; */
  width: 20%;
  border-radius: 48px;
  background-color: white;
}

.about {
  margin-left: 1em;
  align-self: center;
  margin-top: 0;
}

.about > p {
  margin: 0;
}

.track {
  margin-top: 1em;
}

@media only screen and (min-width: 768px) {
  .container {
    display: grid;
    grid-template-columns: repeat(4, auto);
    grid-template-rows: 1fr 1fr;
    grid-gap: 1em;
  }

  h3 {
    display: block;
  }

  .personContainer {
    grid-column: 1/2;
    grid-row: 1/3;
    padding: 0;
    display: grid;
    grid-template-rows: 1fr 1fr 1fr;
  }

  .person {
    grid-row: 1/3;
    display: block;
    margin-top: 0;
    align-items: center;
  }

  .about {
    margin: 0;
    margin-top: 2em;
  }

  img {
    text-align: center;
    padding: 0;
  }

  .time {
    display: block;
    margin-top: 0;
    background-color: hsl(235, 46%, 20%);
    grid-row: 3/4;
  }

  .time > button {
    display: block;
    margin: 0.5em;
  }

  .track {
    grid-column: span 1;
    grid-row: span 1;
    margin-top: 0;
  }
}
</style>
