<template>
  <div class="main_container">
    <div class="top_nav">
      <div class="nav_icon">AUX 奥克斯</div>
      <div class="nav_title">AUX系统地图</div>
      <div class="nav_day">已监控多少天：98天</div>
    </div>
    <div class="left_container">
      <div class="system-distribution-map-wrapper">
        <system-dsitribution-map></system-dsitribution-map>
      </div>
      <div class="system-list-wrapper">
        <system-list></system-list>
      </div>
    </div>
    <div class="right_container">
      <div class="log-list-wrapper">
        <log-list></log-list>
      </div>
      <div class="display-map-wrapper">
        <display-map></display-map>
      </div>
      <div class="log-list-wrapper">
        <log-list></log-list>
      </div>
    </div>
  </div>
</template>

<script>
import SystemDsitributionMap from "@/components/SystemDistributionMap.vue";
import SystemList from "@/components/SystemList.vue";
import LogList from "@/components/LogList.vue";
import DisplayMap from "@/components/DisplayMap.vue";

export default {
  name: "Mainview",
  components: {
    SystemDsitributionMap,
    SystemList,
    LogList,
    DisplayMap
  },
  methods: {},
  created() { },
  data() {
    return {};
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="stylus">
.main_container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgb(8, 32, 65);
  box-sizing: border-box;
  padding: 50px 20px 20px 20px;
  display: flex;
  color: white;

  .top_nav {
    display: flex;
    position: absolute;
    left: 20px;
    right: 20px;
    top: 0;
    height: 50px;
    border-bottom: 1px solid rgba(255, 255, 255, 0.3);

    .nav_icon {
      width: 25%;
      line-height: 50px;
      font-size: large;
      font-weight: bolder;
      text-align: left;
      color: rgba(255, 255, 255, 0.7);
      text-shadow: 5px 5px 5px #000000;
    }

    .nav_title {
      width: 50%;
      line-height: 50px;
      font-size: xx-large;
      color: rgba(255, 255, 255, 0.8);
    }

    .nav_day {
      width: 25%;
      line-height: 50px;
      text-align: right;
      color: rgb(248, 204, 70);
    }
  }

  .left_container {
    position: relative;
    width: 70%;
    height: 100%;
    border-right: 1px solid rgba(255, 255, 255, 0.3);

    .system-distribution-map-wrapper {
      position: absolute;
      top: 0;
      bottom: 145px;
      width: 100%;
      border-bottom: 1px solid rgba(255, 255, 255, 0.3);
      box-sizing: border-box;
    }

    .system-list-wrapper {
      position: absolute;
      bottom: 0;
      height: 145px;
      width: 100%;
      overflow: hidden;
    }
  }

  .right_container {
    width: 30%;
    height: 100%;
    padding-left: 15px;

    .log-list-wrapper {
      width: 100%;
      height: 25%;
      margin: 20px 0;
      border-bottom: 1px solid rgba(255, 255, 255, 0.3);
    }

    .display-map-wrapper {
      width: 100%;
      height: 40%;
      margin: 20px 0;
      border-bottom: 1px solid rgba(255, 255, 255, 0.3);
    }
  }
}
</style>
