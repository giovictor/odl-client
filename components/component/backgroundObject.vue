<template>
  <img :id="id" class="backgroundObject" :src="src" :style="backgroundObjectPositions">
</template>

<script>
export default {
  name: 'BackgroundObject',
  props: {
    id: { type: String, required: true },
    src: { type: String, required: true },
    left: { default: 0 },
    right: { default: 0 },
    top: { default: 0 },
    bottom: { default: 0 },
  },
  computed: {
    backgroundObjectPositions() {
      let positions = {}
      if(this.top) {
        this.$set(positions, 'top', this.top)
      } else {
        this.$set(positions, 'bottom', this.bottom)
      }

      if(this.left) {
        this.$set(positions, 'left', this.left)
      } else {
        this.$set(positions, 'right', this.right)
      }
      return positions
    }
  }
}
</script>

<style>
  .backgroundObject {
    position: absolute;
  }
</style>
