<template>
  <div class="home">
    <arm msg="Arm" :percentage="percentage"/>
    <input type="range" min="0" max="100" step="0.1" v-model="percentage" />
  </div>
</template>

<script>
// @ is an alias to /src
import arm from '@/components/arm.vue'

export default {
  name: 'home',
  components: {
    arm
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
