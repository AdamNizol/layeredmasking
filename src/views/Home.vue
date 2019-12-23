<template>
  <div class="home">
    <div style="display: flex; flex-direction: row; align-items: center; justify-content: center;">
      <arm :percentage="percentage"/>
      <heart :percentage="percentage" />
    </div>
    <input type="range" min="0" max="100" step="0.1" v-model="percentage" />
  </div>
</template>

<script>
// @ is an alias to /src
import arm from '@/components/arm.vue'
import heart from '@/components/heart.vue'

export default {
  name: 'home',
  components: {
    arm, heart
  },
  data(){
    return {
      percentage: 100
    }
  }
}
</script>

<style lang="scss">

</style>
