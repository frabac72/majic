<template>
  <div id="app">
    <!--img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/-->
    <table>
      <tr><td><Header v-bind:tabs='myTabs' v-on:switch-to="switchBody" :key="newBody"></Header>  </td></tr>
      <tr><td><Body v-bind:activeTab="activeTab"></Body></td></tr>
      <tr><td></td></tr>
    </table>
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import Header from './components/header/Header'
import Body from './components/body/Body'
import enums from './util/enums'

export default {
  name: 'app',
  data: function() {
    return {
      myTabs: enums.tabs,
      activeTab: ''
    }
  },
  components: {
    Header,
    Body
  },
  methods : {
    switchBody(newtab) {
      this.activeTab = newtab
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
