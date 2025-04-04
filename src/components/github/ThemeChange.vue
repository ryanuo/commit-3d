<template>
  <div class="themeSelected">
    <BottomIcon title="主题选择" :click="selectTheme" :buttonStyle="btnStyle">
      <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 1024 1024">
        <path fill="currentColor"
          d="M870 126H663.8c-17.4 0-32.9 11.9-37 29.3C614.3 208.1 567 246 512 246s-102.3-37.9-114.8-90.7a37.93 37.93 0 0 0-37-29.3H154a44 44 0 0 0-44 44v252a44 44 0 0 0 44 44h75v388a44 44 0 0 0 44 44h478a44 44 0 0 0 44-44V466h75a44 44 0 0 0 44-44V170a44 44 0 0 0-44-44m-28 268H723v432H301V394H182V198h153.3c28.2 71.2 97.5 120 176.7 120s148.5-48.8 176.7-120H842z" />
      </svg>
    </BottomIcon>
  </div>
</template>

<script>
import CONFIG from '@/assets/js/index.js'
import BottomIcon from '@/components/github/BottomIcon.vue'
export default {
  components: {
    BottomIcon
  },
  computed: {
    btnStyle() {
      return {
        backgroundColor: CONFIG.COLORLIST[`theme${this.themeIndex + 1}`][1]
      }
    }
  },
  data() {
    return {
      themeList: Object.keys(CONFIG.COLORLIST),
      themeIndex: 0
    }
  },
  emits: ['theme'],
  methods: {
    selectTheme() {
      const list = this.themeList
      this.themeIndex++
      if (this.themeIndex >= list.length) {
        this.themeIndex = 0
      }

      this.$emit('theme', `theme${this.themeIndex + 1}`)
    }
  }
}
</script>

<style lang="less" scoped>
.themeSelected {
  position: absolute;
  bottom: 5%;
  right: 5%;
  border-radius: 20px;
  cursor: pointer;

  .item_w {
    margin: 1px 0;
    padding: 10px;
    border-radius: 10px;
    text-align: center;
    // color: #fff;
    font-weight: 550;
    width: 100%;
    height: 100%;
  }
}
</style>
