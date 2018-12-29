<template>
  <div id="app">
    <v-app>
      <v-content>
    <HelloWorld msg="Welcome to Your Vue.js App"/>
      </v-content>
    </v-app>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "app",
  components: {
    HelloWorld
  }
};
</script>

<style lang="scss">
html,
body {
  margin: 0;
  padding: 0;
  height: 100%;
}
#app {
}
</style>
