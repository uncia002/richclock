<template>
  <div id="app">
    <!-- <RangeUI/> -->
    <Anime/>
    <Clock/>
    <!-- <ToolBar/> -->
  </div>
</template>

<script>
import RangeUI from './components/RangeUI.vue'
import Clock from './components/Clock.vue'
import ToolBar from './components/ToolBar.vue'
import Anime from './components/Anime.vue'

export default {
  name: 'App',
  components: {
    Clock,
    RangeUI,
    ToolBar,
    Anime
  }
}
</script>

<style>
html{
  height: 100%;
  margin:0;
}
body{
  margin: 0;
  height: 100%;
  background-color:#EEEEEE;
  overflow-y: hidden;
  user-select: none;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: black;
  width: 100%;
  height: 100%;
}
</style>
