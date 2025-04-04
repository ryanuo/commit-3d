<template>
  <button :title="title" class="btn" :style="buttonStyle" @click="handleClick">
    <slot />
  </button>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true
    },
    buttonStyle: {
      type: Object,
      default: () => {
        return {}
      }
    },
    click: {
      type: Function,
      default: () => { }
    }
  },
  computed: {
    buttonClassProp() {
      return this.class
    }
  },
  methods: {
    handleClick() {
      this.click()
    }
  }
}
</script>

<style scoped>
.btn {
  position: fixed;
  bottom: 3rem;
  right: 3rem;
  z-index: 100;
  height: 2.5rem;
  width: 2.5rem;
  border-radius: 50%;
  border: none;
  opacity: 0.2;
  transition: all 0.3s;
  outline: none;
}

button {
  cursor: pointer;
  outline: none;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: transparent;
  /* Hover效果 */
  transition: background-color 0.3s, opacity 0.3s;
}

button:hover {
  background-color: #8883;
  /* 设置hover颜色 */
  opacity: 1;
}
</style>
