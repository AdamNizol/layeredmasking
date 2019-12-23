<template>
  <div class="heartWrapper">
    <div class="heartContainer" @mousemove="mouseMoved" ref="heartContainer" >
      <img src="@/assets/heartTrail.png" class="topLayer" :style="{clipPath: topLayerMask, transition: 'clip-path 0.3s'}" />
      <img src="@/assets/heart.png" class="topLayer" :style="{clipPath: topLayerMask}" />
      <img src="@/assets/heartEmpty.png" class="baseLayer" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'heart',
  props: {
    percentage: {
      default: 100
    }
  },
  methods: {
    mouseMoved(e){
      let position = this.$refs.heartContainer.getBoundingClientRect();
      let relativePosition = {
        x: e.clientX - position.x,
        y: e.clientY - position.y
      }
      this.mousePos = relativePosition;
    }
  },
  data(){
    return {
      mousePos: {x:0, y:0}
    }
  },
  computed:{
    topLayerMask: function(){
      let mouseEllipse = `ellipse(50px 50px at ${this.mousePos.x}px ${this.mousePos.y}px)`
      let box = `polygon(0% 100%, 100% 100%, 100% ${100-this.percentage}%, 0% ${100-this.percentage}%)`
      return box
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.heartContainer{
  height: 60vh;
  position: relative;
  .topLayer, .baseLayer{
    height: 100%;
  }
  .topLayer {
    position: absolute;
  }
}
.heartWrapper{
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
