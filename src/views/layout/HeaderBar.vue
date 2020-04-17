<template>
  <div class="headerStyle">
    <div class="text">
      <i class="iconfont iconhoutailogo"></i>
      <span>{{title}}</span>
    </div>
    <MenuBar />
    <!-- <div class="timeStyle">{{time+' 18℃ 多云'}}</div> -->
    <div class="company">
      <img :src="imgurl" alt />

      <div class="companyname">
        <span class="comText">{{company}}</span>
        <span class="comEn">{{companyEn}}</span>
      </div>
    </div>
  </div>
</template>
<script>
import MenuBar from "./MenuBar";
import img1 from "../../assets/img/1.png";
console.log("img1: ", img1);
export default {
  name: "HeaderBar",
  components: {
    MenuBar
  },
  data() {
    return {
      title: "农业知识图谱",
      time: new Date(),
      imgurl:
        "https://fuss10.elemecdn.com/e/5d/4a731a90594a4af544c0c25941171jpeg.jpeg",
      company: "深圳航天科工集团有限公司",
      companyEn: "SHENZHEN AEROSPACE SCIENCE AND INDUSTRY CORPORATION"
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
    display: flex;
    height: 80px;
    line-height: 72px;
    align-content: center;

    .iconfont {
      margin-left: 14px;
      font-size: 38px;
      color: #13c6e2;
    }
    span {
      font-family: Source Han Sans CN;
      font-size: 20px;
      font-weight: 400;
      margin-left: 4px;
      color: #fff;
    }
  }
  .company {
    display: flex;
    // height: 80px;
    align-items: center;

    img {
      width: 160px;
      height: 80px;
    }
  }
  .companyname {
    display: flex;
    height: 80px;
    flex-direction: column;
    justify-content: center;
    .comText {
      color: #fff;
      font-size: 11px;
    }
    .comEn {
      color: #fff;
      // font-size: 5px;
      width: 250%;
      -webkit-transform-origin-x: 0;
      -webkit-transform: scale(0.5);
      transform: scale(0.4);
      font-size: 12px;
    }
  }

  .timeStyle {
    color: #13c6e2;
    line-height: 80px;
    font-size: 12px;
  }
}
</style>