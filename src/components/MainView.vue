<template>
  <div class="main_container">
    <div class="top_nav">
      <div class="nav_left">
        <span class="nav_left_letter">AUX 奥克斯</span>
      </div>
      <div class="nav_center">
        <div class="nav_center_title">AUX系统地图</div>
        <span class="nav_center_date">2019年2月23日 星期三</span>
        <span class="nav_center_time">04:04:34</span>
      </div>
      <div class="nav_right">
        <div class="nav_right_days">已监控多少天：98天</div>
      </div>
    </div>
    <div class="main_content">
      <div class="main_content_left">
        <div class="block_bg pruduct_sell"></div>
        <div class="block_bg normal_log">
          <log-list></log-list>
        </div>
        <div class="systematic_health"></div>
      </div>
      <div class="main_content_center">
        <div class="system_distribution_title"></div>
        <div class="system_distribution_map">
          <system-distribution-map></system-distribution-map>
        </div>
        <div class="system_call_number">
          <system-call-number-map></system-call-number-map>
        </div>
      </div>
      <div class="main_content_right">
        <div class="block_bg grow_for">
          <display-map></display-map>
        </div>
        <div class="block_bg order_stat"></div>
        <div class="block_bg error_log">
          <log-list></log-list>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SystemDistributionMap from "@/components/SystemDistributionMap.vue";
import SystemCallNumberMap from "@/components/SystemCallNumberMap.vue";
import SystemList from "@/components/SystemList.vue";
import LogList from "@/components/LogList.vue";
import DisplayMap from "@/components/DisplayMap.vue";

export default {
  name: "Mainview",
  components: {
    SystemDistributionMap,
    SystemCallNumberMap,
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
  background: url('../img/bg.jpg');
  background-size: 100% 100%;
  box-sizing: border-box;
  padding: 60px 20px 0 20px;
  display: flex;
  color: white;

  .top_nav {
    display: flex;
    position: absolute;
    left: 20px;
    right: 20px;
    top: 0;
    height: 60px;
    border-bottom: 1px solid rgba(255, 255, 255, 0.3);

    .nav_left {
      width: 25%;
      text-align: left;

      .nav_left_letter {
        line-height: 60px;
        font-size: 30px;
        font-weight: 800;
      }
    }

    .nav_center {
      width: 50%;

      .nav_center_title {
        font-size: 25px;
        margin: 9px auto;
      }

      .nav_center_time {
        color: rgb(232, 102, 43);
      }
    }

    .nav_right {
      position: relative;
      width: 25%;
      text-align: right;

      .nav_right_days {
        position: absolute;
        bottom: 0;
        right: 0;
        color: rgb(232, 102, 43);
      }
    }
  }

  .main_content {
    display: flex;
    width: 100%;
    height: 100%;

    .main_content_left {
      width: 30%;
      height: 100%;

      .pruduct_sell {
        height: 40%;
      }

      .normal_log {
        height: 30%;
      }

      .systematic_health {
        width: 100%;
        height: 30%;
      }
    }

    .main_content_center {
      width: 40%;
      height: 100%;

      .system_distribution_title {
        width: 100%;
        height: 10%;
      }

      .system_distribution_map {
        width: 100%;
        height: 60%;
      }

      .system_call_number {
        width: 100%;
        height: 30%;
      }
    }

    .main_content_right {
      width: 30%;
      height: 100%;

      .grow_for {
        height: 40%;
      }

      .order_stat {
        height: 30%;
      }

      .error_log {
        height: 30%;
      }
    }
  }
}

.block_bg {
  width: 100%;
  background-image: url('../img/formBg.png');
  background-size: 100% calc(100% - 20px);
  background-position: 0 10px;
  background-repeat: no-repeat;
  padding: 20px 0;
  box-sizing: border-box;
}
</style>
