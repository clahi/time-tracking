<template>
  <div class="wholeItem rounded-3" :class="classObject">
    <div class="imagePart rounded-3">
      <img :src="image" alt="" />
    </div>
    <div class="item rounded-3 py-3 py-md-0 my-0 fw-light">
      <div class="left">
        <p class="my-0 fs-6">{{ trackItem.title }}</p>
        <p class="py-0 unicode my-0">&#1475;</p>
      </div>
      <div class="right my-0">
        <h3 class="my-0 fs-1 fw-lighter">
          {{ timeFrame.current}}hrs
        </h3>
        <p class="text-muted my-0 last" v-if="time == 'daily'">
            yesterday - {{  timeFrame.previous  }}hrs
        </p>
        <p class="text-muted my-0 last" v-else>
          Last {{time.slice(0, -2)}} - {{  timeFrame.previous  }}hrs
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["trackItem", "timeFrame", "time"],
  data() {
    return {
      image: require("../assets/icon-" + this.trackItem.title.toLowerCase().split(' ').join('-') + ".svg"),
      first: '',
      second: ''
    };
  },
  computed: {
    classObject() {
      return {
        work: this.trackItem.title.toLowerCase() == "work",
        play: this.trackItem.title.toLowerCase() == "play", 
        study: this.trackItem.title.toLowerCase() == "study", 
        exercise: this.trackItem.title.toLowerCase() == "exercise", 
        social: this.trackItem.title.toLowerCase() == "social", 
        selfCare: this.trackItem.title.toLowerCase() == "self care", 

      }
    }
    
  }
};
</script>

<style scoped>
.wholeItem {
  padding: 0;
  display: flex;
  flex-direction: column;
}

.work {
  background-color:  hsl(15, 100%, 70%);
}

.play {
  background-color:  hsl(195, 74%, 62%);
}

.study {
  background-color:  hsl(348, 100%, 68%);
}

.exercise {
  background-color:  hsl(145, 58%, 55%);
}

.social {
  background-color:  hsl(264, 64%, 52%);
}

.selfCare {
  background-color:  hsl(43, 84%, 65%);
}

.imagePart {
  max-height: 36px;
  overflow: hidden;
  align-self: flex-end;
}

img {
  width: 50px;
}

.item {
  background-color: hsl(235, 46%, 20%);
  flex-grow: 1;
  padding: 0 0.5em;
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: 1fr 1fr;
}

.left {
  margin-left: 0.5em;
  margin-right: 0.5em;
  margin-bottom: 0;
  grid-column: 1/3;
  grid-row: span 1;
  display: flex;
  justify-content: space-between;
  align-self: flex-end;
}

.right {
  margin-left: 0.5em;
  margin-right: 0.5em;
  margin-top: 0;
  grid-column: 1/3;
  grid-row: span 1;
  display: flex;
  justify-content: space-between;
}

.last {
  align-self: center;
}

.right > .unicode {
  margin-left: 80px;
  margin-top: 0;
}

@media only screen and (min-width: 768px) {
  /* Start from Here */

  .item {
    padding-left: 0.5em;
    padding-right: 1em;
    padding-top: 0;
  }

  .right {
    display: block;
  }
}
</style>