<template>
    <div class="center">
      <the-layout class="child"></the-layout>
    </div>
</template>

<script>
import TheLayout from './components/TheLayout.vue'
export default {
  name: 'App',
  components: {
    TheLayout
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  
}
html,body {
  background-color: hsl(226, 43%, 10%);
  display: flex;
  justify-content: center;
  align-items: center;
}

body * + * {
  margin-top: 2em;
}


@media (min-width: 676px) {
  html, body {
    height: 90%;
  }
}
</style>
