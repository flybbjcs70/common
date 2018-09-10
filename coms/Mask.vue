<template>
  <div class="mask-wrap" v-if="show">
    <div class="mask" @click.self="close"></div>
    <div class="mask-content">
      <slot></slot>
    </div>
  </div>
</template>
<script>
  export default {
    props: {
      closeable: {
        type: Boolean,
        default: true
      },
      value: {
        type: Boolean,
        default: false
      }
    },
    watch: {
      value(val, old) {
        this.show = val
      },
      show(val, old) {
        if (val !== old) {
          this.$emit('input', this.show)
        }
      }
    },
    methods: {
      close() {
        this.closeable && (this.show = false)
      }
    },
    data() {
      return {
        show: this.value
      }
    }
  }

</script>

<style>
  .mask-wrap {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 10
  }

  .mask {
    position: absolute;
    top: 0;
    left: 0;
    background: rgba(0, 0, 0, .5);
    width: 100%;
    height: 100%;
    z-index: 1
  }

  .mask-content {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 2;
    white-space: nowrap;
  }

</style>
