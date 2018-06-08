<template>
  <div id="app">
    <v-app id="inspire">
      <v-container grid-list-md text-xs-center>
        <v-layout row wrap>
          <v-flex xs12>
            <v-menu min-width="300px">
              <v-btn slot="activator" fab><v-icon>settings</v-icon></v-btn>
              <v-list>
                <v-list-tile>
                  <v-slider v-model="numFoods" step="1" min="1" max="50" hint="N" persistent-hint ticks thumb-label/>
                </v-list-tile>
              </v-list>
            </v-menu>
          </v-flex>
        </v-layout>
      </v-container>
      {{positions[0]}}
      <v-content id="foods">
        <svg>
          <food v-for="n in positions.length" :position="positions[n-1]" />
        </svg>
      </v-content>
    </v-app>
  </div>
</template>

<script>

import Vue from 'vue'
import Food from './components/Food.vue'


export default {
  name: 'app',
  components: {
    Food
  }, 
  methods: {
  },
  data: function() { 
    return {
      numFoods: 1,
      positions: [[50, 70]]
    }
  },
  mounted () {
    console.log("HI")
    console.log(this);
    var data = this.$data;
    setInterval(
      function() { 
        var p = data.positions[0];
        Vue.set(p, 0, p[0] + 1)
      }, 100);
    
  }
}
</script>

<style> 

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  width: 100vw;
  height: 100vh;
  position: absolute;
  font-size: 50% !important;
}

.menu {
  z-index: 100;
}

#bar {
  left: 15px;
  top: 30px;
}

#foods {
  position: absolute;
  width: 100vw;
  height: 100vh;
  background-color: hsl(60, 80%, 80%);
}

#foods svg {
  width: 100%;
  height: 100%;
}

#controls {
  z-index: 100;
}

.input-group {
  padding-top: 5px;
}

</style>
