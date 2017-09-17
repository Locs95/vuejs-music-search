<template>
  <div id="app" class="container">
      <MusicList />
  </div>
</template>

<script>

import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'


import MusicList from './components/MusicList'

Vue.use(VueAxios, axios)

export default {
  name: 'app',
  components: {
     MusicList
  },
  template: '<MusicList />',
  data: function() {
     return {
        title: 'Music App'
     }
  }
}
</script>

<style>
html,body {
  height: 100%;
}
#app {
  box-shadow: -0.5px 0.5px 10px rgba(9,9,9,0.5);
  min-height: 100%;
}
#search-bar {
  margin-top: 25px;
  margin-bottom: 10px;
}
#music-list .card {
  margin-bottom: 30px;
}
.play-track {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
.play-track-inner {
   position: absolute;
   top: 0;
   left: 0;
   right: 0;
   bottom: 0;
   margin: auto;
   width: 80px;
   height: 80px;
   border-radius: 40px;
   background-color: #000;
   color: #fff;
   padding: 13px 30px;
   font-size: 2em;
   cursor: pointer;
   opacity: 0;
   transition-property: opacity;
   transition-duration: 0.3s;
}
.play-track:hover .play-track-inner {
   opacity: 0.8;
}

@import "./assets/css/bootstrap.min.css"
</style>

