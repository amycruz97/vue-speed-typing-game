<template>
  <div id="app">
   <ui />
  </div>
</template>

<script>
import ui from './components/ui'

export default {
  name: 'App',
  components: {
   ui
  }
}
</script>

<style>
body{
  background: #454955;
 
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;


}
</style>
