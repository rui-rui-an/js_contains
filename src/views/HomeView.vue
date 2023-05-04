<template>
  <div class="home">
    <div class="left" v-if="showLeft">
      <span class="close_btn" @click="closePopup">X</span>
      <span>弹框--点击其他地方可关闭</span>
    </div>
    <div class="left_tag" v-else @click="weakupPopup">唤起弹框</div>
    <div class="right">主题内容区</div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'HomeView',
  computed: {},
  data() {
    return {
      showLeft: true
    };
  },
  created() {
    document.addEventListener('click', this.bodyClick);
  },
  beforeDestroy() {
    document.removeEventListener('click', this.bodyClick);
  },
  mounted() {},
  methods: {
    bodyClick(e) {
      const left = document.querySelector('.left');
      const right = document.querySelector('.right');
      if (left && !left.contains(e.target) && right.contains(e.target)) {
        this.showLeft = false;
      }
    },
    weakupPopup() {
      this.showLeft = true;
    },
    closePopup() {
      this.showLeft = false;
    }
  },
  components: {}
};
</script>
<style lang="less" scoped>
.home {
  height: 100%;
  display: flex;
  .left {
    height: 100%;
    width: 200px;
    background-color: antiquewhite;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    .close_btn {
      position: absolute;
      width: 20px;
      height: 20px;
      text-align: center;
      line-height: 20px;
      top: 0;
      right: 2px;
      cursor: pointer;
    }
  }
  .right {
    height: 100%;
    flex: 1;
    background-color: #d8aeae;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .left_tag {
    width: 50px;
    height: 50px;
    background-color: red;
    position: absolute;
    cursor: pointer;
    left: 0;
    top: 50%;
    transform: translateY(-50%);
    display: flex;
    align-items: center;
    justify-content: center;
  }
}
</style>
