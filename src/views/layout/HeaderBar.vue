<template>
  <div class="headerStyle">
    <h2 class="text">{{title}}</h2>
    <MenuBar />
    <div class="timeStyle">{{time+' 18℃ 多云'}}</div>
  </div>
</template>
<script>
import MenuBar from "./MenuBar";
export default {
  name: "HeaderBar",
  components: {
    MenuBar
  },
  data() {
    return {
      title: "农业知识图谱",
      time: new Date()
    };
  },
  mounted() {
    let _this = this;
    this.timer = setInterval(function() {
      _this.time = new Date().toLocaleString();
    }, 1000);
  },
  beforeDestroy: function() {
    if (this.timer) {
      clearInterval(this.timer);
    }
  },
  created() {},
  methods: {}
};
</script>

<style rel="stylesheet/scss" lang="scss">
.headerStyle {
  background: #0f1629;
  padding: 0 30px;
  display: flex;
  flex: 1;
  justify-content: space-between;
  align-content: center;
  .text {
    font-family: Source Han Sans CN;
    font-size: 24px;
    font-weight: 400;
    margin-left: 12px;
    color: #fff;
    line-height: 80px;
  }

  .timeStyle {
    color: #13c6e2;
    line-height: 80px;
    font-size: 12px;
  }
}
</style>