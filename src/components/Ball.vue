<template>
  <transition>
    <div class="ball-outer" v-bind:style="outerStyleObject">
      {{px}}
      <svg  :height="radius*2" :width="radius*2">
        <circle  :cx="radius" :cy="radius" :r="radius" fill="hsl(180,50%,50%,1)" opacity="1"/>
      </svg>
    </div>
  </transition>
</template>

<script>
import anime from 'animejs'

export default {
  name: 'Ball',
  props: {
    px: {
      default: 100,
      type: Number
    },
    py: {
      default: 100,
      type: Number
    }
  },
  data: function () { 
    return {
    }
  },

  computed: {

    radius: function () {
      return 20;
    },
    outerStyleObject: function () {
      return {
        transform: "translateX(" + (parseInt(this.px)-this.radius) + "px) translateY(" + (parseInt(this.py)-this.radius) + "px)"
      }
    }
  },
  methods: {
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.ball-outer  {
  position: absolute;
}

</style>
