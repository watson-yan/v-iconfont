<template>
  <svg v-if="active" class="icon"
    :style="styleComputed"
    viewBox="0 0 1024 1024" 
    xmlns="http://www.w3.org/2000/svg">
    <path :d="active.d" :fill="color">
    </path>
  </svg>
</template>
<script>
  import svgs from './svgs.js'
  export default {
    props: {
      icon: {
        type: String,
        required: true
      },
      w: {
        type: Number
      },
      color: {
        type: String,
        default: 'inherit'
      }
    },
    data() {
      return {
        list: svgs,
        active: null
      }
    },
    computed: {
      styleComputed() {
        if (!this.w) {
          return {}
        }
        return {
          width: `${this.w}px`
        }
      }
    },
    created() {
      for (let i = 0; i < this.list.length; i++) {
        if (this.list[i] === this.icon) {
          this.active = list[i]
          break
        }
      }
    }
  }
</script>
<style scoped>
  .icon {
    vertical-align: middle;
    fill: currentColor;
    overflow: hidden;
  }
</style>
