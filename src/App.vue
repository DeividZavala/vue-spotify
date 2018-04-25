<template>
  <div id="app">
    <HelloWorld/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import HelloWorld from './components/HelloWorld.vue';

@Component({
  components: {
    HelloWorld,
  },
})
export default class App extends Vue {}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

.spotify-player {
  background: #000000;
  border: 1px solid #666666;
  width: 50%;
  margin: 10px;
  padding: 4px;
  border-radius: 10px;
}

.player:after {
  clear: both;
  content: " ";
  display: block;
}
</style>
